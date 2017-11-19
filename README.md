VSCameraActivity
============


VSCameraActivity is a simple camera2 API Kotlin wrapper class. With basic configuration like open with front or back camera, fullscreen mode, take picture button and a count down until take photo option.


Installation
============


Add `VSCameraActivity.kt` to your project.
Add `activity_vs_camera.xml` to your project inside `layout`.


Setup
=====

Import your package at the top of `VSCameraActivity.kt`.

```
package example.com.myapplication
```

AndroidManifest.xml
-------------------

Add `<uses-feature android:name="com.android.hardware.camera2.full"/>` & `<uses-permission android:name="android.permission.CAMERA"/>` before `<application>`.

Usage
=====

Start a new intent using the convience method `newIntent`.

```
val intent = VSCameraActivity.newIntent(this, isBackCamera = false, isFullScreen = true, isCountDownEnabled = true, countDownInSeconds = 3)
startActivityForResult(intent, VSCameraActivity.VSCAMERAACTIVITY_RESULT_CODE)
```

Override `onActivityResult` to use the returned Bitmap.

```
override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent) {
        if (resultCode == VSCameraActivity.VSCAMERAACTIVITY_RESULT_CODE) {
            var bitmap = VSBitmapStore.getBitmap(data.getIntExtra(VSCameraActivity.VSCAMERAACTIVITY_IMAGE_ID, 0))
            this.imageView.setImageBitmap(bitmap)
        }
    }
```