---
title: "ubuntu 10.10 Crashes when i play media files"
date: 2011-08-27
forum: Multimedia Software
---

### Post by a.clever on 2011-08-27
Hey Guys
I am new to Linux system,i installed Ubuntu 10,10 32bit on Dell XPS L502X dual boot with windows 7.when i`m going to play any media files such as audio or video or flash Ubuntu freezes but mouse cursor still move so i am forced to restart my laptop by pressing power button.
plz help me
and sorry for my bad English.

---

### Post by picolo33 on 2011-08-27
[CENTER][COLOR="Green"]Maybe this problem because of the ISO

Make MD5 to it 

" this step to make sure that the ISO had no problem " 

[click here to know how ]("https://help.ubuntu.com/community/HowToMD5SUM")

[and this is a ubuntu hash list ]("https://help.ubuntu.com/community/UbuntuHashes")[/COLOR][/CENTER]

---

### Post by a.clever on 2011-08-27
I checked MD5 that was 100% true
> MD5:9050d4cd3ae8c98eaef5b694b360e9eb 
    Version:Ubuntu-10.10-DVD-i386.ISO 


so do have another suggestion?

and another question but not related to this topic
i downloaded latest nvidia Geforce 540M for Linux
and tried to install it,i exited x and started to install Driver.
that showed this message:
> THE DISTRIBUTION-PROVIDED PRE-INSTALL *SCRIPT* FAILED,Do you want to continue setup
i choosed yes,and setup started and completed and then asked me to configure x server and i agreed that and setup finished.
but then i couldn't run x,it said it`s running but i couldn't see,i restarted and used recovey option and restored x to previous config,and so i could run x.when i went back to Ubuntu there was nvidia x config but it said > there isn't any config of nvidia for x or something like this

---

### Post by BicyclerBoy on 2011-08-28
Your laptop has optimus graphics & this is problematic for Linux.

You should un-install the nvidia driver & get the machine working with just the intel APU.
It is a bad idea to download & install the nvidia driver from console login..There are many pit-falls & it is not controlled by debian package management system.

It is possible to get the nvidia GPU working using Bumblebee etc..but there are a lot of hurdles in the way.

So make a study of optimus graphics & VGA-switcharoo & Bumblebee..

---

### Post by thewolfman on 2011-08-28
Use the addtional drivers hardware tool which is in the admin list or the control center, download the drivers for Nvidia and select the one which states "recommended.

Regards thewolfman:P

---

