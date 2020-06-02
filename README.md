# react-native-troubleshooting
react-native各种问题以及解决方案

### @react-navigation/native@5 android 手势问题

问题描述：android开启手势功能，键盘弹起输入时，点击屏幕左边的位置会出现键盘收起又弹出的问题

> 解决方法1：关闭android手势功能

> 解决方法2：缩小手势的触发区域，可以通过设置`gestureResponseDistance`实现


### [FlatList靠近屏幕底部的最后一个TextInput无法弹起键盘](https://github.com/facebook/react-native/issues/23916)

问题描述：keyboard dismisses automatically when focused on TextInput inside a Flatlist

> 解决方法：I think that setting FlatList.removeClippedSubviews to false might be a workaround for now.

### 慎用`overflow:"hidden"`

### React-Native Textinput Android键盘无法弹起问题
问题描述  Textinput位于（FlatList,SectionList,ScrollView)的底部 Android键盘无法弹起

解决方法 
第一步：FlatList 新增属性 removeClippedSubviews={Platform.OS === 'ios' ? undefined : false}
第二步：AndroidManifest.xml中的 MainActivity配置中 新增属性 android:windowSoftInputMode="adjustPan"
 eg:```<activity
                android:name=".MainActivity"
                android:configChanges="keyboard|keyboardHidden|orientation|screenSize|uiMode"
                android:label="@string/app_name"
                android:launchMode="singleTask"
                android:windowSoftInputMode="adjustPan">
            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>
                <category android:name="android.intent.category.LAUNCHER"/>
            </intent-filter>
        </activity>```
 ### 慎用FastImage
 问题描述 React-Native Android在部分手机上 和overflow 一起使用会出现 页面透传问题
 解决办法：
 新增属性 tintColor={(isFocused || Platform.OS === 'ios') ? undefined : '#F5F6F7'}
 不使用overflow

