---
title: "Pixel C Infinite Reboot / Ubuntu 16.04"
date: 2018-04-21
forum: Mobile Technology Discussions (CLOSED)
---

### Post by AnotherBrian on 2018-04-21
Spent the day fussing around on getting a Pixel C Tablet running again.  Just posting this in case it helps someone.  

The device was never visible using abd but was visible using fastboot. 

Symptoms were that I got the triangle with ! mark with robot on its side.  adb and fastboot (there are several) loaded through Ubuntu 16.04 repositories never worked for me. 
 
Instead load this software which includes the latest adb and fastboot from google: [developer.android.com/studio/releases/platform-tools.html]("https://ubuntuforums.org/developer.android.com/studio/releases/platform-tools.html")
In a shell execute: 
> 
sudo su
export PATH=$PATH:/home/YOURUSERNAME/platform-tools
where of course the software is loaded in that directory.  

Next download the tablet software and unzip: [developers.google.com/android/images]("https://ubuntuforums.org/developers.google.com/android/images")
Then go to that directory (it was ryu<complicatedName> and execute the command in the zip file: 
> cd /home/YOURUSERNAME/Downloads/ryu*
./flash-all.sh


Now on tablet push power_button and volume_down_button a long time until screen goes blank, release, wait, and then see the linux shell start downloading.

---

### Post by bijayalaxmi1808 on 2018-06-14
If you want a step-by-step guide then here is the following sequence:
- Unlock the bootloader on Pixel C
- Then download the stock Android Image of Pixel C and flash them using Fastboot

Here are few of the resources that explains more in-detail:
- [URL="https://www.cyanogenmods.org/forums/topic/unlock-bootloader-google-nexus-pixel/"]How to Unlock Bootloader on Google Pixel Phones
[/URL]- [URL="https://www.cyanogenmods.org/forums/topic/stock-unroot-nexus-return-stock-flash-factory-image/"]How to Install Stock Android Image on Pixel Device
[/URL]
Installing the stock image requires Fastboot:
[how to install Fastboot on Linux]("https://www.cyanogenmods.org/forums/topic/install-adb-fastboot-linux-mac-os-x/")

---

