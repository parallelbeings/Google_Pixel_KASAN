
----------
## To resolve the touchscreen issue after building AOSP with KASAN + KCOV in the pixel device. 

### Method 1:
To follow the steps suggested in the updated blog post for pixel 3, https://blog.senyuuri.info/2021/03/01/fixing-android-drivers-post-treble/. 

### Method 2: 
I found a way to update the kernel drivers to persist after reboot for the touch screen issue in my Pixel 4XL.

- adb root
- adb remount -R
- adb shell
- rm *.ko /vendor/lib/modules
- Copy all the *.ko files from the branch/kasan folder to /vendor/lib/modules

The branch I used was https://android.googlesource.com/device/google/coral-kernel/+/refs/tags/android-11.0.0_r34/kasan/. I downloaded the driver files from the KASAN folder and copied it to the modules folder. 
Now after every boot, the new kernel modules were loaded successfully. 
