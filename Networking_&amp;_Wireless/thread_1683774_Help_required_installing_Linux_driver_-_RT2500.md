---
title: "Help required installing Linux driver - RT2500"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by Jim Hornet on 2011-02-08
I have found a Linux driver for the RT2500 but I  am have trouble with command bit (still getting my head around it) - I  get stuck at 3. 
 
Installing linux driver instructions: 
1) Uncompress file (using nautilus: right click > uncompress). 
2) Open a terminal. 
3) Navigate to the folder that you just extracted (if you extracted the  zipped file to /home/user (where user is your user name) and the folder  is called (RTLDRIVERS) this would be: cd /home/user/RTLDRIVERS. 
4) sudo su 
5) make 
6) make install 
7) reboot. 
 
I downloaded driver RT25USB-SRC-V2.0.8.0.ta..gz I uncompressed it in my  Home Folder - when I uncompressed it the file/folder name is  
RT25USB-SRC-V2.0.8.0.ta so..... 
 
At 3 I type in: cd/homeuser/RT25USB-SRC-V2.0.8.0.ta  Enter 
 
and I get command not found or does not exist - what am I doing wrong - am I writing in the wrong command. 
 
Please Help 
 
I am trying to get my self up to speed with basic command but struggling 
 
I have typed in ls in the terminal and the file is there - I am confused 
 
 
should I just use the ndiswrapper program and see if that fixes my wifi card.  
 
PS - My network is picked up by Ubuntu 10.10 but every time I go to  connect - it goes through the connecting process but never connects???

---

### Post by theDaveTheRave on 2011-02-08
it looks as though the file that you downloaded

RT25USB-SRC-V2.0.8.0.ta..gz

hasn't been uncompressed properly.

I'm making the assumption from your join date and number of beans you are a newb (welcome to the forums), so I may be a bit verbose for your skill level, apologies in advance.

My suggestions is this.

on your home directory make a new directory for the RT... download

```

mkdir RT2500
[code]

download the file again from the same location (may be an idea to double check the [MD5 checksum]("http://https://help.ubuntu.com/community/HowToMD5SUM"), if it has been given one, to ensure it isn't corrupted on its way - especially if you keep getting errors)

Using nautilus / terminal or your preferred file manager, move the file into the new directory.

Back at the terminal cd into the new directory, then 'untar' the file... (I am assuming the name of the file that you gave earlier)

[code]
cd RT2500

```
note that your prompt will now have changed

and 'untar' the archive...
```

tar -xvf RT25USB-SRC-V2.0.8.0.tar.gz

```

you will now most likely see a bunch of stuff fly through the screen, if you get any errors post them here and we'll try to help out.

Now you should be able to do the following
```

ls

```
and see the old compressed file, and now a nice new directory having been created (probably called RT25USB-SRC-V2.0.8.0), now you can use a nice timesaving trick to get into the directory...
```

cd R

```

now press the tab key and the directory will be automagically completed for you, if not, press it again and it will show you all the directories that begin with 'R' (then just type in enough to make it  unique and press the tab to auto complete it).

Now you have changed into this directory you can follow the rest of your original guide... However I wouldn't
```

sudo su

```

I would do the following...

```

sudo make
sudo make install

```

now reboot and see if you are working.

David

---

### Post by Jim Hornet on 2011-02-08
Hi David - I followed your instructions - I unpacked the file and it seemed like it worked - I went to put in the ls command no new folder was created only the original RT25USB-SRC-V2.0.8.0 (extracted file) and RT25USB-SRC-V2.0.8.0.ta. (tar file) and the downloaded file RT25USB-SRC-V2.0.8.0.ta..gz in my RT2500 folder I created.  

And yes I am new to Ubuntu/Linux and appreciate your help   

> [COLOR=Red]:[COLOR=Black]~$ cd RT2500 [/COLOR]
:[COLOR=Black]~/RT2500$ tar -xvf RT25USB-SRC-V2.0.8.0.ta. [/COLOR][/COLOR]
RT25USB-SRC-V2.0.8.0/ 
RT25USB-SRC-V2.0.8.0/sha1.h 
RT25USB-SRC-V2.0.8.0/Makefile.4 
RT25USB-SRC-V2.0.8.0/rt2570sw.h 
RT25USB-SRC-V2.0.8.0/readme 
RT25USB-SRC-V2.0.8.0/rtmp_wep.c 
RT25USB-SRC-V2.0.8.0/md5.h 
RT25USB-SRC-V2.0.8.0/auth_rsp.c 
RT25USB-SRC-V2.0.8.0/wpa.c 
RT25USB-SRC-V2.0.8.0/rtusb.h 
RT25USB-SRC-V2.0.8.0/rtmp_type.h 
RT25USB-SRC-V2.0.8.0/Configure 
RT25USB-SRC-V2.0.8.0/Stdincl.h 
RT25USB-SRC-V2.0.8.0/rtusb_init.c 
RT25USB-SRC-V2.0.8.0/mlme.c 
RT25USB-SRC-V2.0.8.0/rtusb_data.c 
RT25USB-SRC-V2.0.8.0/config.mk 
RT25USB-SRC-V2.0.8.0/ReleaseNote 
RT25USB-SRC-V2.0.8.0/oid.h
RT25USB-SRC-V2.0.8.0/rtusb_bulk.c 
RT25USB-SRC-V2.0.8.0/auth.c
 RT25USB-SRC-V2.0.8.0/md5.c 
RT25USB-SRC-V2.0.8.0/rt2570.h 
RT25USB-SRC-V2.0.8.0/wpa.h
 RT25USB-SRC-V2.0.8.0/Makefile.6 
RT25USB-SRC-V2.0.8.0/Makefile 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/Oid.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/sha1.h
 RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/DebugPrint.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/qhexvalidator.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ProfilePage.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/readme 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/RaPropSheet.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/configapi.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ui/
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ui/raconfigui.ui 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ui/AddProfile.ui 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ui/authsecudlg.ui 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ui/security.ui 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ui/hiddenssiddlg.ui 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/AdvancePage.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/sha1.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/raconfig2500.pro 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ids.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/RaPropSheet.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/qhexvalidator.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/rt_tool.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/AboutPage.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/hiddenssiddlg.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/RaConfig2500.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/AboutPage.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/StatisticPage.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/cardselect.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/authsecudlg.h
 RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/addprofiledlg.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/StructDef.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ico/ 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ico/adapter.xpm
 RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ico/uncheck16.xpm 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ico/handshak16.xpm 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ico/rtlogo.png 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ico/radiooff.png 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ico/radioon.png 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ico/RaConfig2500.xpm 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ico/noactive16.xpm
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ico/check16.xpm
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/hiddenssiddlg.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/authsecudlg.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/Makefile
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/SiteSurvPage.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/DebugPrint.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/countryform.cpp
 RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/rt_tool.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/ProfilePage.cpp
 RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/LinkStatusPage.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/configapi.cpp
 RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/AdvancePage.cpp 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/LinkStatusPage.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/addprofiledlg.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/StatisticPage.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/SiteSurvPage.h
 RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/countryform.h 
RT25USB-SRC-V2.0.8.0/LINUX_RACONFIG_V2.0.0.7/cardselect.h 
RT25USB-SRC-V2.0.8.0/sync.c RT25USB-SRC-V2.0.8.0/rt_config.h 
RT25USB-SRC-V2.0.8.0/rtmp_tkip.c 
RT25USB-SRC-V2.0.8.0/rtusb_info.c 
RT25USB-SRC-V2.0.8.0/rtusb_main.c 
RT25USB-SRC-V2.0.8.0/mlme.h 
RT25USB-SRC-V2.0.8.0/sanity.c 
RT25USB-SRC-V2.0.8.0/assoc.c 
RT25USB-SRC-V2.0.8.0/connect.c 
RT25USB-SRC-V2.0.8.0/rtmp_ckipmic.h 
RT25USB-SRC-V2.0.8.0/iwpriv_usage.txt 
RT25USB-SRC-V2.0.8.0/rtmp_def.h 
RT25USB-SRC-V2.0.8.0/rtusb_io.c 
[COLOR=Red]:[/COLOR]~/RT2500$ ls 
RT25USB-SRC-V2.0.8.0  RT25USB-SRC-V2.0.8.0.ta.  RT25USB-SRC-V2.0.8.0.ta..gz 
:~/RT2500$ cd R bash: cd: R: No such file or directory [COLOR=Red]
[/COLOR]:~/RT2500$ 
 [COLOR=Red]:[/COLOR]~/RT2500$ RT25USB-SRC-V2.0.8.0 RT25USB-SRC-V2.0.8.0: command not found [COLOR=Red]
:[/COLOR]~/RT2500$ tar -xvf RT25USB-SRC-V2.0.8.0.tar..gz tar: 
RT25USB-SRC-V2.0.8.0.tar..gz: Cannot open: No such file or directory tar: Error is not recoverable: exiting now
 [COLOR=Red]:[/COLOR]~/RT2500$ Any ideas what I have done wrong?   Thanks

---

### Post by chili555 on 2011-02-08
> Any ideas what I have done wrong? ThanksYes. A variety of typos. The file was successfully extracted:```
spaznuts@spaznuts:~/RT2500$ tar -xvf RT25USB-SRC-V2.0.8.0.ta.
RT25USB-SRC-V2.0.8.0/
RT25USB-SRC-V2.0.8.0/sha1.h
RT25USB-SRC-V2.0.8.0/Makefile.4
RT25USB-SRC-V2.0.8.0/rt2570sw.h
RT25USB-SRC-V2.0.8.0/readme
RT25USB-SRC-V2.0.8.0/rtmp_wep.c
RT25USB-SRC-V2.0.8.0/md5.h
RT25USB-SRC-V2.0.8.0/auth_rsp.c
RT25USB-SRC-V2.0.8.0/wpa.c
RT25USB-SRC-V2.0.8.0/rtusb.h 
etc., etc.
```Now, to build the module, simply do:```
cd RT25USB-SRC-V2.0.8.0
make
sudo make install
```However, why are you doing so? The rt2500usb drivers are already a part of the normal Ubuntu install:```
modinfo rt2500usb
```If your device isn't working out of the box, either rt2500usb is not correct for the device or something else is wrong.

---

### Post by Jim Hornet on 2011-02-09
Hi Chili555, 
 
Thanks for clarification, I have not yet been able to get a wi fi connection with my card - I have no probs on the XP OS but when it comes to UBUNTU 10.10 I cannot connect - My network is detected and it tries to connect with no joy.
 
My card is a RALINK RT2500 USB WLAN 54Mbit/s IEEE 802.11g/ 802.11b compatible.(fairly old)
 
I didnt know that this card was supported already so I tried the Linux driver RT25USB-SRC-V2.0.8.0.ta..gz - there is another Ralink2500 driver that isnt USB - I will try that next.
 
If that fails I will have to stick with the ehernet connection or maybe a new card. Thanks for your help - I will try what you suggested with commands and will post back with result. 
 
Thanks very much 
 
Jim

---

### Post by chili555 on 2011-02-09
Let's try to troubleshoot what you already have. First, let's see which exact device you have. Please run and post:```
lsusb
```Now, let's see what drivers are loading:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard along with \. 

Now let's see if there are any informative kernel messages:```
dmesg | grep -i rt2
```Our systems have trouble with mixed WPA and WPA2 mode; please be sure your router is set to one or the other, not mixed.

---

### Post by theDaveTheRave on 2011-02-10
seems like you are getting the required assistance from chili555

I wasn't aware that this usb device was supported by the default Ubuntu, sorry for that, maybe you have don't extra stuff that wasn't neccesary.

If I can help in any way I will do so, but for now chili555 seems to have you going in the direction I would have sent you anyway, so I'll leave you in what are likely to be his more capable hands.

good luck.

David.

---

### Post by Jim Hornet on 2011-02-10
Hi David and Chilli, 

Thanks for the help so far - I am very grateful and getting used to commands slowly slowly. Chilli I have posted the info below on my wifi

> [COLOR=Black]:[/COLOR]~$ modinfo rt2500usb
filename:       /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
license:        GPL
description:    Ralink RT2500 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     5CD1249E10E9B6A4F2C1AAF
alias:          usb:v5A57p0260d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F88p3012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p11F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v114Bp0110d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0707pEE13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0681p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v079Bp004Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2570d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp1706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6869d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6865d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0097d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p008Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0067d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p005Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p001Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1706d*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2x00usb
vermagic:       2.6.35-25-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
[COLOR=Black]
:[/COLOR]~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:00bb Microsoft Corp. Fingerprint Reader
Bus 002 Device 002: ID 04fc:0015 Sunplus Technology Co., Ltd ViewMate Desktop Mouse CC2201
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 001 Device 006: ID 148f:2570 Ralink Technology, Corp. RT2570 Wireless Adapter
Bus 001 Device 005: ID 0d8c:5200 C-Media Electronics, Inc. Mass Storage Controller(0D8C,5200)
Bus 001 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=Black]spaznuts@spaznuts:[/COLOR]:~$ lsmod | grep rt2
rt2500usb              18049  0 
rt2x00usb               9779  1 rt2500usb
rt2x00lib              27275  2 rt2500usb,rt2x00usb
led_class               2633  1 rt2x00lib
mac80211              231959  2 rt2x00usb,rt2x00lib
cfg80211              144694  2 rt2x00lib,mac80211
[COLOR=Black]
:[/COLOR]~$ dmesg | grep -i rt2
[   14.301894] Registered led device: rt2500usb-phy0::radio
[   14.301922] Registered led device: rt2500usb-phy0::quality
[   14.302801] usbcore: registered new interface driver rt2500usb
Any thoughts? 

I have also changed my router to WPA2 PSK from WPA+WPA2 PSK as you have suggested

---

### Post by chili555 on 2011-02-10
> :~$ modinfo rt2500usb
filename: /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
license: GPL
description: Ralink RT2500 USB Wireless LAN driver.
version: 2.3.0
author: [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion: 5CD1249E10E9B6A4F2C1AAF
alias: usb:v5A57p0260d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0F88p3012d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0EB0p9020d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0769p11F3d*dc*dsc*dp*ic*isc*ip*
alias: usb:v114Bp0110d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0707pEE13d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0681p3C06d*dc*dsc*dp*ic*isc*ip*
alias: usb:v079Bp004Bd*dc*dsc*dp*ic*isc*ip*
alias: usb:v148Fp9020d*dc*dsc*dp*ic*isc*ip*
alias: usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias: usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]2570[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias: usb:v148Fp1706d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0DB0p6869d*dc*dsc*dp*ic*isc*ip*
alias: usb:v0DB0p6865d*dc*dsc*dp*ic*isc*ip*> Bus 001 Device 006: ID [COLOR="Red"]148f[/COLOR]:[COLOR="Red"]2570[/COLOR] Ralink Technology, Corp. RT2570 Wireless AdapterIt's the correct driver for your device, it attaches and appears perfectly normal. Since you changed to WPA2 only, does it connect or time out?

---

### Post by Jim Hornet on 2011-02-10
Hi Chilli thanks for quick reply

I went to reboot and still no joy - I might have to buy a new wifi card - Thanks for your help

I hate being a noob but now I have another problem I cant get into my XP LOL - steep learning curve

[http://ubuntuforums.org/showthread.php?t=1685367](http://ubuntuforums.org/showthread.php?t=1685367)

Thanks Chilli and David Much appreciated

---

