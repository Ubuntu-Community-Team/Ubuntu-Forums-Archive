---
title: "How to install ROOT, Custom Recovery &amp; Custom Roms (via ADB) on Android (via Linux)"
date: 2016-06-01
forum: Mobile Technology Discussions (CLOSED)
---

### Post by jake007g2 on 2016-06-01
Hi everybody, thought I'd make my first post a useful one. 

I've always tweaked software on all my devices - and the other day I set about upgrading my Samsung Galaxy S6 Edge to Marshmallow from Lollipop with a custom rom. I spent hours trawling through many pages on the internet to find the information I needed which was a pain - especially as there are so many how-to guides for Windows users. So I thought I'd share what I've learnt with the community to give a bit back!

If you've never heard of 'Root', 'Custom Recovery' (such as TWRP) or 'Custom Roms' until now - I suggest spending a bit of time researching them before jumping in the deep end.

[B]ROOT = SU Privileges
Custom Recovery (TWRP) = How we install Custom Roms & fix things if you brake them
Custom Roms = An unofficial modified version of Android (usually debloated/faster/better battery etc) [/B]

As with anything of this nature, there is a chance you could brick your device (I will not be held responsible so _**PLEASE**_ ensure you know what you're doing!).

Please also ensure that any important data on your device (such as photos/contacts/app data) is backed up before going any further.

Now there are a few files you're going to need before we get started - and these files will be individual for your device. In this guide I will be using a Samsung Galaxy S6 Edge (SM-G925F UK Variant) on Stock Marshmallow 6.0.1 for reference. The process for most devices/android versions is the same - all though the files you'll need to flash will vary depending on your device's **Model **and **Android Version.**

Please head to settings>about device(>software info) on Android to find out anything you need to know. Whilst you're in your 'About Device' settings - tap on the 'Build Number' quickly about 10 times to enable Developer options, and head into them on the main settings page & enable 'USB Debugging'.

**ROOT**
[LIST]
[*]Firstly, download ROOT files for your device. You can find these by searching google - for example in my case: "G925F 6.0.1 Root". If you get a zip file please extract it and look for a .TAR file (if it's a .TAR.MD5 extension simply delete the .MD5 as the checksum isn't needed here). For reference's sake I'll refer to this file as **root.tar** throughout the guide. 
[*]Please create a new folder within your home directory and name it "android". 
[*]Place **root.tar **in /home/android 
[*]Open terminal (CTRL ALT + T) and navigate to /home/android with **cd android** 
[*]Via terminal we're going to extract **root.tar **with **tar -xvf root.tar** 
[*]Once extracted you should be presented with **boot.img **(if not please try downloading another root kernel in Odin format _.tar_*.md5*) 
[*]Back in terminal, please install Heimdall flash (linux alternative to Odin) **sudo apt-get install heimdall-flash** 
[*]Once installed, run **lsusb **command to list USB devices 
[*]Power off your phone then hold down **Volume Down, Center Home, and Power  buttons** together for about 5 seconds until you enter download mode and plug into your computer (may be different key combo for different phones to my G925F). 
[*]Run **lsusb** again and check there's an extra entry (for your phone in download mode). 
[*]Now, in terminal, run: **heimdall flash --BOOT boot.img** 
[*]All being successful your phone should reboot with its' new root kernel (Download SuperSU off play store to check root status and to individually grant SU privileges to apps). 
[/LIST]

**Custom Recovery**
[LIST]
[*]Firstly, download CUSTOM RECOVERY files for your device. You can find these by  searching google - for example in my case: "G925F 6.0.1 TWRP". If you  get a zip file please extract it and look for a .TAR file (if it's a  .TAR.MD5 extension simply delete the .MD5 as the checksum isn't needed here). For reference's sake I'll refer to this file as **twrp.tar** throughout the guide. 
[*]Place **twrp.tar **in /home/android (the folder we made in the rooting process) 
[*]Open terminal (CTRL ALT + T) and navigate to /home/android with [B]cd android
[/B] 
[*]Via terminal we're going to extract **twrp.tar **with **tar -xvf twrp.tar** 
[*]Once extracted you should be presented with **recovery.img **(if not please try downloading another custom recovery in Odin format _.tar_*.md5*) 
[*]Power off your phone then hold down Volume Down, Center Home, and Power  buttons together for about 5 seconds until you enter download mode and  plug into your computer (may be different key combo for different phones  to my G925F). 
[*]Run **lsusb **and ensure your phone in download mode is recognised by Linux as you did in the rooting process. 
[*]Now, in terminal, run: **heimdall flash --RECOVERY recovery.img** 
[*]If everything went to plan, your phone should reboot as normal. 
[*]Power off your phone then hold down **Volume Up, Center Home, and Power  buttons** together for about 5 seconds until you enter your custom recovery (TWRP in this case). 
[/LIST]
[B]
Custom Roms[/B] via **ADB**
Now with custom roms, you could always install them the simple way (add rom zip file to device internal storage, boot TWRP recovery and install from there). 

In this guide I'll show you how to install them via **ADB Sideload **on Linux. This is very useful if you mess something up and cannot access your device's internal storage!


[LIST]
[*]Firstly download your **Custom Rom **zip file. You can find these by  searching google - for example in my case: "G925F 6.0.1 Custom Rom". If you  get a zip file then this is the correct format to flash and it doesn't need extracting. I chose the Tyrannus Rom on XDA forums By frenkowski (Brilliant rom - recommend trying it if you can). For reference's sake I'll refer to this file as **customrom.zip** throughout the guide. 
[*]Place your **customrom.zip **in the /home/android folder which we've used previously and navigate to it in terminal with **cd android** 
[*]Staying in terminal, please install the adb tools needed with **sudo apt-get install adb** 
[*]To be on the safe side, we will declare some generic rules for main  Android phones manufacturers. These rules will be declared  /etc/udev/rules.d/51-android.rules. To declare these rules simply run  the following two commands in terminal one after the other: **sudo wget -O /etc/u[COLOR=#000000]dev/rules.d/51-android.rules  [/COLOR][[COLOR=#000000]https://raw.githubusercontent.com/NicolasBernaerts/ubuntu-scripts/master/android/51-android.rules[/COLOR]]("https://raw.githubusercontent.com/NicolasBernaerts/ubuntu-scripts/master/android/51-android.rules")** followed by **sudo chmod a+r /etc/udev/rules.d/51-android.rules **(full credit given to NicolasBernaerts for hosting the file) 
[*]We can now restart udev for the new rules to become operational. Run **sudo service udev restart** in terminal. 
[*]Now run **lsusb **to display connected USB devices. 
[*]Power off your phone then hold down **Volume Up, Center Home, and Power  buttons** together for about 5 seconds until you enter your custom recovery (TWRP in this case). 
[*]Once TWRP custom recovery has loaded, head to **Advanced**, plug your micro USB into your computer and click **ADB Sideload. **I'd also recommend wiping the Dalvik Cache and Cache before sideloading. 
[*]Now in terminal, run **lsusb **again to ensure your computer is recognising the device in ADB Sideload mode. 
[*]If all has gone well up to here - you are ready to install your custom rom. To do this, simply sideload it with **adb sideload customrom.zip **in terminal. Most custom roms include an on-screen installer which you need to go through on your device. 
[/LIST]

**I hope you've found this guide useful. I give full credit to everybody referenced in the guide.**

---

### Post by Jonners59 on 2016-09-05
Just tried this on my new S7 SM-G930F but it failed.
The official root is CF-AutoRoot-herolte-heroltexx-smg930f.zip and which I named root.tar so the comands were easy.  Within it there are two files cache.img and recovery.img

It downloaded but then stopped and I got the error message "Setting up interface...libusb: error [op_set_interface] setintf failed error -1 errno 110
ERROR: Setting up interface failed!
Releasing device interface..."

and on the phone it says
"An error has occurred while updating the device software.  Use Emergency recovery function in Smart Switch PC Software".

Can you help, please?  Where have I gone wrong?

---

### Post by mike-chunkmedia on 2016-09-29
Hi, great post thank you. I tried to put CyanogenMod onto my Nexus 4 last night. I got the customrom.zip onto the phone and then accidentally wiped the partitions. I can now boot the phone into CyanogenMod Recovery mode but my Ubuntu 16.04 LTS laptop won't see the phone. When I run lsusb the phone is not listed. And when I run abd sideload I get the message "no device found". Any ideas how I might get abd sideload to transfer the customrom.zip onto my phone? Thanks, Mike

---

### Post by vocx on 2016-12-30
This thread is a fantastic summary of how to modify your phone with Linux, thank you.

I have updated some parts in a post below.
> **vocx said:**
> I decided to reformat and rewrite some parts of the guide from the beginning of this thread.

Since this thread may come up in future searches on Heimdall on Linux, I want to point out a problem that is encountered with many Samsung phones as of 2016.

As seen in other threads on the [internet]("https://android.stackexchange.com/questions/130392/heimdall-error-protocol-initialisation-failed-on-ubuntu") ([2]("https://forum.xda-developers.com/showthread.php?t=2661069"), [3]("https://github.com/Benjamin-Dobell/Heimdall/issues/228"), [4]("https://github.com/Benjamin-Dobell/Heimdall/issues/364")), some people report the error
```

ERROR: Failed to receive handshake response. Result: -7
ERROR: Protocol initialisation failed!

```
and are unable to transfer any custom recovery (TWRP, CWM), or complete images (CyanogenMod) to their devices. Not even printing the PIT (partition index table) information works.

To solve this issue the threads commonly propose two solutions

[LIST=1]
[*]Installing the latest Heimdall, and 
[*]Making sure the phone is not recognized as a modem by "udev" 
[/LIST]

For the first solution they recommend installing developer tools such as
```
sudo apt-get install build-essential cmake zlib1g-dev qt5-default libusb-1.0-0-dev libgl1-mesa-glx libgl1-mesa-dev
```
and compiling Heimdall in your own system. The program "[heimdall]("http://glassechidna.com.au/heimdall/")" has existed since [2012]("https://bitbucket.org/benjamin_dobell/heimdall/downloads") at least, but it seems the source code has not changed much since 2014, when v1.4.1 was released. You could follow the [Github page]("https://github.com/Benjamin-Dobell/Heimdall/") for further development.

Compiling should be a matter of downloading the project folder and then
```

mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make

```

For the second solution, they suggest editing a file
```

sudo nano /etc/udev/rules.d/79-samsung.rules

```

and adding the following lines
```

SUSBSYSTEM=="usb", ATTRS{idVendor}=="04e8", ATTRS{idProduct}="685d", MODE="0666", GROUP="plugdev"
SUSBSYSTEM=="usb", ATTRS{idVendor}=="04e8", ATTRS{idProduct}="685d", ENV{ID_MM_DEVICE_IGNORE}="1"

```
The first line identifies a connected USB device by the vendor ID "04e8" (corresponding to Samsung), product ID "685d" (corresponding to Galaxy SII, and other similar phones), sets the mode to "0666", meaning read and write access for the owner, group and others, and sets the group to "plugdev". This may help with reading and writing to the device.

The second line again identifies the vendor and product, and sets a property to "1", to avoid recognizing the device as a modem. This may be helpful if the kernel messages given by "dmesg" show something like this
```

[25117.873244] cdc_acm 2-1.3:1.0: This device cannot do calls on its own. It is not a modem.

```
Otherwise only the first line may be necessary.

After saving that file you should restart the "udev" service, or just restart the computer, for the changes to take place
```

sudo service udev restart

```
 The specific vendor and product number can be seen in the output 04e8:6860 of the "lsusb" command, and in the kernel messages obtained from "dmesg"
```

Bus 002 Device 022: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)

```
```

[29199.511138] usb 2-1: new high-speed USB device number 22 using xhci_hcd
[29199.640254] usb 2-1: New USB device found, idVendor=04e8, idProduct=6860
[29199.640257] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[29199.640259] usb 2-1: Product: SAMSUNG_Android
[29199.640260] usb 2-1: Manufacturer: SAMSUNG
[29199.640262] usb 2-1: SerialNumber: eea0c257

```

Despite performing these steps, it seems this is not a solution for everybody. For many people Heimdall simply won't connect to the phone when it's in download mode.

This seems to be a problem mostly with phones based on the Qualcomm Snapdragon (S4 series) MSM8960 system on chip, as seen from the kernel messages. This affects many S and A models, and possibly other phones.
```

[25117.780287] usb 2-1.3: new high-speed USB device number 15 using ehci-pci
[25117.872818] usb 2-1.3: New USB device found, idVendor=04e8, idProduct=685d
[25117.872823] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[25117.872827] usb 2-1.3: Product: MSM8960
[25117.872829] usb 2-1.3: Manufacturer: Sasmsung
[25117.873244] cdc_acm 2-1.3:1.0: This device cannot do calls on its own. It is not a modem.
[25117.873313] cdc_acm 2-1.3:1.0: ttyACM0: USB ACM device

```

In my case, I couldn't make it work in Linux, so I had to borrow a Windows 10 computer to flash the custom recovery image using the Windows-only [Odin program]("https://forum.xda-developers.com/showthread.php?t=2711451"), as is described in instructions found elsewhere.

Remember that programs in Linux use underlying system libraries that are different from those in Windows. In particular, this may not be a problem with Heimdall, but with the underlying "libusb" library, on which Heimdall depends.

---

### Post by vocx on 2016-12-31
I decided to reformat and rewrite some parts of the guide from the beginning of this thread. Credit goes to jake007g2 for the original guide.

> **jake007g2 said:**
> Hi everybody, thought I'd make my first post a useful one. 

**1. Introduction**
I've always tweaked software on all my devices, and the other day I set about upgrading my Samsung Galaxy S6 Edge to Marshmallow (6.0) from Lollipop (5.0) with a custom ROM. I spent hours trawling through many pages on the Internet to find the information I needed which was a pain, especially as there are so many how-to guides for Windows users. So I decided to make a guide using only Linux.

If you've never heard of "root", "rooting", "custom recovery" or "custom ROMs" until now, I suggest spending a bit of time researching them before jumping in the deep end.

[LIST]
[*]**Root**: obtaining "root", or "rooting", means acquiring "super user" privileges. It allows you to modify every file of your device, including system files. It is similar to using "sudo" in Ubuntu. Most devices in the market don't come rooted, which means by default you are unable to thinker with many components of your device. 
[*]**Custom recovery**: how we install, change, erase, back up, and restore custom ROMs, and fix things if you break them. Using a "custom recovery application" is like using a live CD or USB drive that allows you to change things before booting into the actual system. The most popular recovery applications are ClockworkMod Recovery (CWM) and Team Win Recovery Project (TWRP). 
[*]**Custom ROM**: an unofficial, modified version of the Android operating system with tweaks to make it faster, use different themes, and have functionality normally not found in stock mobile phones. It's the equivalent of a Linux distribution, you can install one ROM that suits your needs, and even make your own. 
[/LIST]

**2. Disclaimer**
[LIST]
[*]As with anything of this nature, there is a chance that you damage your device. If your device does not boot into the home screen, or is stuck rebooting, this is called "bricking", that is, your device does not work any more, except as a paper weight or brick. 
[*]I will not be held responsible for this so PLEASE ensure you know what you're doing! 
[*]Just like a desktop or laptop computer, if you brick a mobile phone it is usually possible to make it work again, you just have to repair or reinstall the operating system. 
[*]Please ensure that any important data on your device, such as photos, contacts, and app data, is backed up before going any further. If you have a Google or Samsung account, it is a good idea to synchronize your data before proceeding. 
[/LIST]

**3. Requirements**
[LIST]
[*]There are a few files you're going to need, these files will be specific for your device. In this guide I will be using a Samsung Galaxy S6 Edge (SM-G925F UK Variant) on stock Marshmallow 6.0.1 for reference. The process for most devices is the same, but you will need the files for your device's model. 
[*]In your device, head to "**Settings**" > "**About device**" to find out model number and other important information. You will need to search on the internet for your "**Model number**", which looks like "SM-G925F", "GT-I9300", "SM-G530H", etc. 
[*]Do not search for the commercial name such as "Galaxy S6 Edge", "Galaxy S III", "Galaxy Grand Prime", etc., as the manufacturer may release several times the same phone, but with different firmware. 
[*]Whilst you're in the "**About device**" screen, go into "**Software info**" and tap on the "**Build number**" about 10 times to enable "**Developer options**". 
[*]Go back to the "**Settings**" screen and enter "**Developer options**". Make sure the main slider is enabled at the top of the screen, and also the options "**USB debugging**" and "**OEM unlock**" are enabled. Some devices don't have "**OEM unlock**", so ignore it in this case. 
[*]Install **Heimdall**. You can do it from the repository, or compile your own. Heimdall allows you to flash (write) the custom recovery images and ROMs  into the device. It is the Linux alternative to the Windows-only tool, **Odin**.
```

sudo apt-get install heimdall-flash heimdall-flash-frontend

``` 
[*]Install the **Android Debug Bridge** (adb), which is used to communicate with a connected Android device. A custom ROM can be installed using a custom recovery application (which you have to install first), or using "**adb**", as explained here.
```

sudo apt-get install adb

``` 
[*]Connect your device with an USB cable to the computer, and run "**lsusb**", to make sure your device is recognized.
```

Bus 002 Device 025: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)

``` 
[*]To be on the safe side, we will declare some generic "udev" rules for main Android phones manufacturers. Create and edit this file
```

sudo nano /etc/udev/rules.d/51-android.rules

```
Add the following line
```

# Samsung
SUBSYSTEM=="usb", ATTR{idVendor}=="04e8", MODE="0666", GROUP="plugdev"

```
What this does is taking a USB device from vendor 04e8 (Samsung), changing the mode to read-write for everybody (0666), and setting its group to "plugdev". This should help with accessing the device with "**heimdall**" and "**adb**". You can add as many rules as you want by adding a new line with the appropriate "idVendor" number, which appears in the output of "**lsusb**". 
[*]If you prefer, you can run the following two commands to download a file with many rules. The file, which you can inspect [here]("https://raw.githubusercontent.com/NicolasBernaerts/ubuntu-scripts/master/android/51-android.rules") before downloading, already includes many rules for different vendors. Full credit is given to NicolasBernaerts for hosting the file.
```

sudo wget -O /etc/udev/rules.d/51-android.rules https://raw.githubusercontent.com/NicolasBernaerts/ubuntu-scripts/master/android/51-android.rules
sudo chmod a+r /etc/udev/rules.d/51-android.rules

``` 
[*]Restart "udev", or reboot the computer, for the new rules to become operational
```

sudo service udev restart

``` 
[/LIST]

**4. Modes**
Your phone needs to be in certain modes to perform certain steps in **5. Root**, **6. Custom recovery**, and **8. Custom ROMs**.

**4.1. System mode**
It is the normal mode of the phone. With the phone turned off, just turn it on, and let it reach the home screen.

**4.2. Download mode**
It allows you to flash images to the internal memory of the phone.
[LIST]
[*]With your phone turned off, hold down **Volume Down**, **Center Home**, and **Power** buttons together for about 5 seconds. This will show you a screen warning you about installing operating systems. 
[*]Press the **Volume up** button to continue and enter "**Download mode**" (also called "**Odin mode**"). In this screen you will see information but won't be able to do anything else. The button combination to enter this mode may be different in other devices. 
[*]If you entered "**Download mode**" and you  simply want to go out of it, press and hold the same button combination as  before or simply remove the battery from your device. 
[*]With the phone in "**Download mode**", connect your device with the USB cable to the computer, and run "**lsusb**", to make sure your device is recognized.
```

Bus 002 Device 026: ID 04e8:685d Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II] (Download mode)

``` 
[/LIST]

Many guides talk about entering "**Fastboot mode**" and the command "**fastboot**" for flashing images. Newer phones don't have "Fastboot". Instead there is "**Download mode**" and flashing is done with "**heimdall**".

**4.3. Recovery mode**
It allows you perform certain recovery operations on the phone without booting into the system.
[LIST]
[*]With your phone turned off, hold down **Volume Up**, **Center Home**, and **Power** buttons together for about 5 seconds. This will launch the recovery application. 
[*]If you have a custom recovery application, like TWRP or CWM, it will start. Otherwise it will start the stock Android recovery application, which is very basic. 
[/LIST]

**5. Root**
[LIST]
[*]In many cases you don't need to perform these instructions to obtain root. You can try doing **6. Custom recovery** first. 
[*]Download root files for your device to your computer. You can find these by searching on the internet, for example, in my case "G925F 6.0.1 Root". If you get a zip file please extract it and look for a "**.tar**" file. If it's a "**.tar.md5**" extension simply delete the "**.md5**" part of the name as the checksum isn't needed here. For reference's sake I'll refer to this file as "**root.tar**" throughout the guide. The root image contains a small kernel that is installed only once to allow access to root functions. Expect a small file, ranging from 3 MB to 10 MB in size. 
[*]Extract "**root.tar**"
```

tar -xvf root.tar

``` 
[*]Once extracted you should be presented with "**boot.img**". If this file is not present try downloading another root kernel. 
[*]Follow **4.2. Download mode** to enter "**Download mode**" in your device. 
[*]Now flash the "**boot.img**" from the computer terminal
```

heimdall flash --BOOT boot.img

``` 
[*]If everything went fine, your phone should reboot into the normal system with its new root kernel. If it doesn't, press and hold the same button combination to enter "**Download mode**" to reboot. 
[*]Now you can go to the Play Store and download "Root Checker" and "SuperSU", or another application of your choice, to check root status and to manage super user permissions for applications. 
[/LIST]

**6. Custom recovery**
[LIST]
[*]Download the custom recovery image for your device. You can find these by searching on the internet, for example, in my case "G925F 6.0.1 TWRP", for the TWRP recovery image. If you get a zip file please extract it and look for a "**.tar**" file. If it's a "**.tar.md5**" extension simply delete the "**.md5**" part of the name as the checksum isn't needed here. For reference's sake I'll refer to this file as "**twrp.tar**" throughout the guide. The custom recovery image contains a small application that is only accessible when the phone boots up. Expect a small file, ranging from 8 MB to 20 MB in size. 
[*]Extract "**twrp.tar**"
```

tar -xvf twrp.tar

``` 
[*]Once extracted you should be presented with "**recovery.img**". If this file is not present try downloading another custom recovery file. 
[*]Follow **4.2. Download mode** to enter "**Download mode**" in your device. 
[*]Now flash the "**recovery.img**" from the computer terminal
```

heimdall flash --RECOVERY recovery.img

``` 
[*]If everything went fine, your phone should reboot. If it doesn't, press and hold the same button combination to enter "**Download mode**" to reboot. 
[*]As it reboots, immediately hold down **Volume Up**, **Center Home**, and **Power** buttons together for about 5 seconds to enter "**Recovery mode**" and see the newly installed recovery application (TWRP in this case). 
[*]If you don't manage to enter "**Recovery mode**", turn off your phone and try again the button combination. If you are presented with the standard Android recovery application, it is possible that the flashing was successful but upon reboot the standard recovery image was rewritten by the system. In this case, repeat the steps: turn off the phone, enter "**Download mode**", and flash "**recovery.img**" once more. 
[/LIST]

**6.1. Custom recovery and root**
[LIST]
[*]You may install "SuperSU" directly from the recovery application and obtain root access in this way, without performing the instructions on **4. Root**. 
[*]Search on the internet for the installable SuperSU zip file, which we'll call "**SuperSU.zip**", and download it to your phone (SD card or internal memory). 
[*]Complete **6. Custom recovery**, and enter TWRP as indicated in **4.3. Recovery mode**. 
[*]Install "**SuperSU.zip**" by navigating to where it was downloaded. 
[*]Reboot and log in to the home screen normally. You can now go to the Play Store and upgrade "SuperSU", or install another application of your choice, to manage super user permissions for applications. 
[/LIST]

**7. Some notes**
[LIST]
[*]The command "**heimdall**" flashes (writes) the indicated image into the partition specified by the command line option "**--PARTITION**". Be sure this is the correct one when you perform this step. 
[*]You can also use a Heimdall frontend to flash the images, but the command line is certainly faster.
```

sudo heimdall-frontend

``` 
[*]For the "**heimdall-frontend**", go to "**Utilities**", choose the name of the file, and click "**Download** to save the PIT file to disk. Then switch to the "**Flash**" tab, add the corresponding PIT file, browse to the corresponding image file, select the appropriate partition, and then click "**Start**" to flash the image. 
[*]The button combination to enter "**Download mode**" has **Volume Down**, while to enter "**Recovery mode**" has **Volume Up**. 
[*]Once you install a custom recovery application such as TWRP, you can use it to install ROMs, apps, do backups, and upgrade itself. In general, you only need to access "**Download mode**" if you wish to flash a new recovery image and you cannot do this from TWRP itself. This may be necessary if a system update or ROM installation rewrites the custom recovery image with the stock Android recovery image. 
[/LIST]

**8. Custom ROMs**
[LIST]
[*]First follow **6. Custom recovery** to install a custom recovery image (we assume TWRP). 
[*]Download your custom ROM zip file. You can find these by searching the internet, for example in my case "G925F 6.0.1 Custom Rom". If you  get a zip file then this is the correct format to flash and it doesn't need extracting. For reference's sake I'll refer to this file as "**customrom.zip**" throughout the guide. Custom ROMs include the main components of the system so expect a large file, ranging from 400 MB to 1000 MB in size, depending on what it actually contains. 
[/LIST]

**8.1. With custom recovery.** In this method you don't need the computer anymore, you can install the ROM directly from your phone.
[LIST]
[*]Transfer "**customrom.zip**" to the SD card or internal memory of your phone, or download it directly here. 
[*]Enter "**Recovery mode**" as indicated in **4.3. Recovery mode**. 
[*]Install "**customrom.zip**" by navigating to where it was downloaded (SD card or internal memory). 
[/LIST]

**8.2. With ADB sideload.** This is very useful if you mess something up and cannot access your device's internal storage!
[LIST]
[*]Enter "**Recovery mode**" as indicated in **4.3. Recovery mode**. 
[*]Once TWRP has loaded, head to "**Advanced**", connect your device with the USB cable to the computer, and click "**ADB Sideload**". I'd also recommend wiping the "**Dalvik Cache**" and "**Cache**" before sideloading. 
[*]Now in terminal, run "**lsusb**" again to ensure your computer is recognising the device in "**ADB Sideload**" mode.
```

Bus 002 Device 028: ID 18d1:d002 Google Inc.

``` 
[*]If all has gone well run in the computer terminal
```

adb sideload customrom.zip

``` 
[*]Most custom ROMs include an on-screen installer which you need to go through on your device. 
[/LIST]

---

### Post by Robbyx on 2017-08-07
In my phone and I believe all models of  Samsung phones the Model No, IMEI, and S/N is to be found behind the battery. No need to search for model number on the internet.

---

### Post by Robbyx on 2017-08-07
I am unable to get into recovery mode although it was there when i did a prior install of CM13 mod. Now I only get the download mode and I can not boot the phone (samsung GT-i860)

I took the boot.img out of latest unofficial codina_full at [https://forum.xda-developers.com/galaxy-ace/ace-2-develop/rom-cyanogemod-13-sergeyl-t3277418/post71325836#post71325836](https://forum.xda-developers.com/galaxy-ace/ace-2-develop/rom-cyanogemod-13-sergeyl-t3277418/post71325836#post71325836)

I think what is going wrong is the SD1 drive is being looked at in the heimdall flash below and found to be missing a boot drive because it is on SD0. The prior version of the ROM was installed by me with the two modifications offered one of which is to swap memory so that SD1 becomes SD0 see [https://forum.xda-developers.com/galaxy-ace/ace-2-develop/rom-cyanogemod-13-sergeyl-t3277418](https://forum.xda-developers.com/galaxy-ace/ace-2-develop/rom-cyanogemod-13-sergeyl-t3277418)

The build I used below is the version of the ROM that does not swap memories.


Any idea what to do with this error?

heimdall flash --BOOT boot.img

Beginning session...

Some devices may take up to 2 minutes to respond.
Please be patient!

Session begun.

Downloading device's PIT file...
PIT file download successful.

ERROR: Partition "BOOT" does not exist in the specified PIT.
Ending session...
Rebooting device...
Releasing device interface...

---

