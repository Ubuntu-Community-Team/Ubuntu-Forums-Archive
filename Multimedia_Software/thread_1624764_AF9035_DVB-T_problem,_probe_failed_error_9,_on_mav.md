---
title: "AF9035 DVB-T problem, probe failed error 9, on maverick"
date: 2010-11-18
forum: Multimedia Software
---

### Post by kuro_man on 2010-11-18
Hi, 

I have a clean install of mythbuntu 10.10 and I am trying to get a DVB-T USB stick working for the last 2 weeks.  Its a MobiDTV and it seems to have the same chipset/USB ID as EzCap_DVB_T_Stick.

I followed the instructions on the [http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick](http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick) and eventually got the driver compiled (I had to amend some code, change "Bool" pointers to "bool" and add a FIRMWARE MAX_NAME 30 constant).  I also copied the af9035 FW file to the firmware directory.

**lsusb:**
Bus 002 Device 004: ID 15a4:1001 Afatech Technologies, Inc. AF9015/AF9035 DVB-T stick

but it is not working; probe is failing:
**dmesg:**
[  105.104195]         DRIVER_RELEASE_VERSION : v2.0-1
[  105.104203]         FW_RELEASE_VERSION     : v8_8_52_0
[  105.104209]         API_RELEASE_VERSION    : 200.20081203.0
[  105.110713] [Device_init] Error 1
[  105.110733] ***dvb_usb_af903x: probe of 2-5:1.1 failed with error 9***

Any help greatly appreciated! 

I am a tech-savvy but new to Linux so I may not know relatively simple things.  I bought the hardware with Windows 7 MCE in mind.  I have no Windows 7 disk so I installed Mythbuntu on it to see if build was solid and now I don't want Windows any more.

---

### Post by kuro_man on 2010-11-22
I haven't fixed this problem, but I did recompile the driver with the latest header (.h) files from v4l-dvb and this helped.  It has removed the error 9, now giving err -22, invalid argument. 
 
I think this is only a patch away but its beyond my limited C skills
 
Anyway, I buggered up my install messing so I have re-installed maverick.

---

### Post by polomint77 on 2011-01-28
Hi,

  Did you ever manage to get the usb stick to work?  I have the exact same stick and have no idea where to start.

  Thanks.

---

