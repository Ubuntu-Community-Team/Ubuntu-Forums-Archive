---
title: "Faults and Failures, Installing Ubuntu on Tablet/Phone"
date: 2013-02-21
forum: Mobile Technology Discussions (CLOSED)
---

### Post by e8hffff on 2013-02-21
Currently getting error on my Nexus 7 freshly flashed with latest 4.2.2 image;

```

Starting new HTTP connection (1): cdimage.ubuntu.com
Download directory set to /home/Downloads/phablet-flash/95
Device detected as /sbin/sh: getprop: not found
Unsupported device, autodetect fails device

```Do I need to install BusyBox in Android to get 'getprop' command?

I'm about to check net for the file and I maybe able to adb push the it. I'm also going to try booting the device for first time to see if it builds files in the process then try to flash Ubuntu's files in.

---

### Post by lprofil on 2013-02-21
How did you "freshly flash" it?

/lprofil

---

### Post by e8hffff on 2013-02-21
> **lprofil said:**
> How did you "freshly flash" it?

/lprofil

Well I had Plasma Active on it.  I downloaded proper image from Google and unzipped the archive where the images were.  I used fastboot to flash the partitions and all is working fine with Android 4.2.2.

---

### Post by e8hffff on 2013-02-21
I'm now manually installing using Ubuntu, and having android tools preinstalled. My device is already OEM cracked and  has ClockWorkModRecovery installed. Google to get this stage if you're unfamiliar.

**Get the following files from;**

[http://cdimage.ubuntu.com/ubuntu-touch-preview/quantal/mwc-demo/](http://cdimage.ubuntu.com/ubuntu-touch-preview/quantal/mwc-demo/)

[LIST]
[*]quantal-preinstalled-boot-armel+grouper.img
[*]quantal-preinstalled-armel+grouper.zip
[*]quantal-preinstalled-phablet-armhf.zip
[/LIST]
Boot nexus into fastboot mode, which is from device off stage. That means holding power button and volume button at same time till you see the repair mode, not the recovery. Make sure usb in plugged in.

Now open a terminal where your files downloaded to and do the following;

Type "fastboot flash boot ./quantal-preinstalled-boot-armel+grouper.img"

The image should flash the boot partition.  Once done use the controls (vol +/-) to select recovery mode and then press the power button to choose. You should boot into recovery mode.

Now select 'install zip using sideloader' option.  Now you can send the files;

Type "adb sideload ./quantal-preinstalled-phablet-armhf.zip"

Wait for device to work on the zip then do sideload for;

Type "adb sideload ./quantal-preinstalled-armel+grouper.zip"

Now if you reboot you should have the goods. Enjoy!


**Known problems:**

Sometimes devices are blocked on Ubuntu from detecting on the USB.  You'll need to add a rule line to the exceptions;

/etc/udev/rules.d/51-android.rules

add lines if not there;

```

# fastboot protocol on the grouper (Nexus 7)
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e40", MODE="0600", OWNER="default"

# mtp protocol on the grouper (Nexus 7)
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e41", MODE="0600", OWNER="default"

# adb protocol on the grouper (Nexus 7)
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e42", MODE="0600", OWNER="default"

# adb protocol on the grouper (Nexus 7)
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="d001", MODE="0600", OWNER="default"

```

You can 'lsusb' to get the vendor id  and product id, if your device isn't supported in the list!

---

### Post by lprofil on 2013-02-21
> **e8hffff said:**
> I'm now manually installing using Ubuntu

Why would you do that?

The "Touch Developer Preview Tools" did the job quiet well for me
after figuring out that you don't need to boot the device in recovery mode but just plain an simply running android.
Took me an hour until i found out why adb could not work that way :P.

Tomorrow i want to figure out how to get a working dualboot system.
[Here you have some information about it]("http://forum.xda-developers.com/showthread.php?t=2011403") but i couldn't get it working yet with the tablet version. 
Though the Desktop version of Ubuntu ran fine aside Android.

/lprofil

---

### Post by gustavopepi on 2013-07-04
I rooted my brand new nexus 4,  to install the ubunto phone and then a followed these steps [https://wiki.ubuntu.com/Touch/Install](https://wiki.ubuntu.com/Touch/Install) and in step 4, after the ¨[COLOR=#333333]phablet-flash -b¨, it started to get ubuntu phone, and then this massage appeared

[/COLOR]Error while executing adb push /home/gustavo/Downloads/phablet-flash/ubuntu-touch/20130704.2/saucy-preinstalled-touch-armhf.zip /sdcard/autodeploy.zipMake sure the device is connected and viewable by running 'adb devices'
Ensure you have a root device, one which running 'adb root' does not return an error

and then the phone don´t start any more, get stuck in these screen 
[https://www.dropbox.com/sc/3qz8ia05ybdswdy/AWbCQZppEc](https://www.dropbox.com/sc/3qz8ia05ybdswdy/AWbCQZppEc)
and get stuck in these screen.

---

### Post by Nr90 on 2013-07-07
That dropbox album appears empty.
Anyway when one of my flashes failed I sideloaded android to fix my device.
Don't remember the exact steps, I just googled sideloading.

---

