---
title: "Mvix Solido driver (rtl8712/8172) on 10.04"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by joshruehlig on 2010-04-30
[http://www.mvixusa.com/product/solido](http://www.mvixusa.com/product/solido)

I got it working on 9.10 by...

unpacking, cd into driver folder, unpack folder inside that
sudo su, make, make install, ./clean, insmod 8712u.ko

It then worked, upon restart, I had to run a script that ran ./clean, insmod 8712u.ko, and restart usb
I put this into /etc/init.d/rc.local...
[B]
Now in 10.04 when running make I get [/B]
----------------------------------------------
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.32-21-generic/build M=/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/cmd/rtl871x_cmd.o
In file included from /home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/cmd/rtl871x_cmd.c:21:
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h: In function ‘thread_enter’:
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:361: error: implicit declaration of function ‘daemonize’
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:362: error: implicit declaration of function ‘allow_signal’
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:362: error: ‘SIGTERM’ undeclared (first use in this function)
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:362: error: (Each undeclared identifier is reported only once
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:362: error: for each function it appears in.)
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h: In function ‘flush_signals_thread’:
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:369: error: implicit declaration of function ‘signal_pending’
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:371: error: implicit declaration of function ‘flush_signals’
In file included from include/linux/usb.h:21,
                 from /home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_intf.h:13,
                 from /home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/rtl871x_io.h:7,
                 from /home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/drv_types.h:58,
                 from /home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/cmd/rtl871x_cmd.c:22:
include/linux/sched.h: At top level:
include/linux/sched.h:2037: warning: conflicting types for ‘flush_signals’
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:371: note: previous implicit declaration of ‘flush_signals’ was here
include/linux/sched.h:2151: warning: conflicting types for ‘daemonize’
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:361: note: previous implicit declaration of ‘daemonize’ was here
include/linux/sched.h:2349: error: static declaration of ‘signal_pending’ follows non-static declaration
/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/include/osdep_service.h:369: note: previous implicit declaration of ‘signal_pending’ was here
make[2]: *** [/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/joshua/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [modules] Error 2
--------------------------------------------------
I tried this with both 
rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091112.p4 (from cd)
rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202 (from online)
----------------------------
lsusb
Bus 001 Device 008: ID 0bda:8172 Realtek Semiconductor Corp. 
----------------------------
When on Wireless Networks says "device not ready"

Thank you, I just wonder why it worked for 9.10 but not 10.04. Maybe it's the kernel?

---

### Post by darwinev0lved on 2010-04-30
Well I'm glad it's not just me. This is driving me potty. Don't want to have to use ndiswrapper but may have to. 
 I try make and get this:

make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.32-21-generic/build M=/home/jon/Downloads/rtl8712/driver/rtl8712  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/jon/Downloads/rtl8712/driver/rtl8712/cmd/rtl871x_cmd.o
In file included from /home/jon/Downloads/rtl8712/driver/rtl8712/cmd/rtl871x_cmd.c:21:
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h: In function ‘thread_enter’:
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h:355: error: implicit declaration of function ‘daemonize’
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h:356: error: implicit declaration of function ‘allow_signal’
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h:356: error: ‘SIGTERM’ undeclared (first use in this function)
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h:356: error: (Each undeclared identifier is reported only once
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h:356: error: for each function it appears in.)
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h: In function ‘flush_signals_thread’:
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h:363: error: implicit declaration of function ‘signal_pending’
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h:365: error: implicit declaration of function ‘flush_signals’
In file included from include/linux/usb.h:21,
                 from /home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_intf.h:13,
                 from /home/jon/Downloads/rtl8712/driver/rtl8712/include/rtl871x_io.h:7,
                 from /home/jon/Downloads/rtl8712/driver/rtl8712/include/drv_types.h:58,
                 from /home/jon/Downloads/rtl8712/driver/rtl8712/cmd/rtl871x_cmd.c:22:
include/linux/sched.h: At top level:
include/linux/sched.h:2037: warning: conflicting types for ‘flush_signals’
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h:365: note: previous implicit declaration of ‘flush_signals’ was here
include/linux/sched.h:2151: warning: conflicting types for ‘daemonize’
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h:355: note: previous implicit declaration of ‘daemonize’ was here
include/linux/sched.h:2349: error: static declaration of ‘signal_pending’ follows non-static declaration
/home/jon/Downloads/rtl8712/driver/rtl8712/include/osdep_service.h:363: note: previous implicit declaration of ‘signal_pending’ was here
make[2]: *** [/home/jon/Downloads/rtl8712/driver/rtl8712/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/jon/Downloads/rtl8712/driver/rtl8712] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [modules] Error 2


Which looks almost (exactly?) the same. Any advice much appreciated.

---

### Post by joshruehlig on 2010-04-30
You have the same usb wifi as me? the one with the antenna? I like so much about lucid but it can't make wifi drivers from karmic...

I used ndiswrapper before and it ran good, but we have the linux drivers for this thing!!! Good we can attack this thing head on together, I wont have internet access this weekend but Ill start trying stuff next monday.

We may need to compile a new kernel. If you have a chance get a live cd (or running desktop) of karmic and build the module and save the output, thanks.

Heres another thread with very similar problems
[http://ubuntuforums.org/showthread.php?t=960113&page=5](http://ubuntuforums.org/showthread.php?t=960113&page=5)

looks like something we need to file on a bug report, i dont know how...
__________________

---

### Post by darwinev0lved on 2010-04-30
> **joshruehlig said:**
> You have the same usb wifi as me? the one with the antenna? I like so much about lucid but it can't make wifi drivers from karmic...

I used ndiswrapper before and it ran good, but we have the linux drivers for this thing!!! Good we can attack this thing head on together, I wont have internet access this weekend but Ill start trying stuff next monday.

Heres another thread with very similar problems
[http://ubuntuforums.org/showthread.php?t=960113&page=5](http://ubuntuforums.org/showthread.php?t=960113&page=5)

looks like something we need to file on a bug report, i dont know how...

Not sure it's the same exactly, no antennae on mine - but it is the 0bda:8172 Realtek usb wifi, so it's the same chip inside. I've got it going using ndiswrapper. I'm not a linux guru, so any help is appreciated. There have been others who've got the 8192 working 

[http://ubuntuforums.org/showthread.php?t=1267961&page=3](http://ubuntuforums.org/showthread.php?t=1267961&page=3)

- but nothing I've tried yet has helped. grump. Still, have a good weekend and hopefully we can fix this.
I'm going to give up on it tonight, but I may try putting 9.10 on a usb stick and seeing if I can't build the module tomorrow.

---

### Post by joshruehlig on 2010-04-30
Just got it working with ndiswraper. ill see if theres a performance difference. Thanks

---

### Post by joshruehlig on 2010-05-03
ndiswrapper seems to work fine, but it requires I use my wifi switch to turn on and off my wifi after a resume or thaw. I wrote a script and placed it in /usr/lib/pm-utils/ so I wouldn't have to.
------------------
#!/bin/sh

case $1 in
    resume|thaw)
     echo -n "usb1" > /sys/bus/usb/drivers/usb/unbind
     echo -n "usb1" > /sys/bus/usb/drivers/usb/bind
    ;;
esac
exit 0
------------------
sudo chmod +x /etc/pm-utils/76usbwifi

I named it 76 so it would run after 75modules, but I'm not sure if I could make it earlier safely and decrease network searching time after login.

I read a little in the thread you gave and we might be missing some build packages? I'm thinking of marking this solved if I dont find anything within a few days

---

### Post by joshruehlig on 2010-06-06
Solved for native driver thanks to this guy [http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html)

---

### Post by joshruehlig on 2010-07-09
UPDATE!

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

The new update supports 2.6.33... which I guess means the directions provided with the driver work perfectly with Lucid. You don't even need to sudo apt-get install, just follow the install instructions. My earlier link is no longer needed.

---

### Post by Cariboo1938 on 2010-11-11
> **joshruehlig said:**
> UPDATE!

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

The new update supports 2.6.33... which I guess means the directions provided with the driver work perfectly with Lucid. You don't even need to sudo apt-get install, just follow the install instructions. My earlier link is no longer needed.
On the site above are several chip-sets and corresponding Linux drivers listed, i.e. 
Date 2010/6/30 for RTL8191SU, RTL8188SU, RTL8192SU, 
Date 2010/10/25 for RTL8191SE-VA2, RTL8192SE, 
Date 2010/10/20 for RTL8192CU, RTL8188CUS, 
Date 2010/10/15 for RTL8188CE, and RTL8192CE-VA4. 
Which is the new driver update needed for [COLOR="Red"][SIZE="3"]ID 0bda:8172 Realtek Semiconductor Corp.?[/SIZE][/COLOR]

---

### Post by moviglez on 2010-11-20
Try this attachment

---

### Post by rocksockdoc on 2011-04-24
For the record, I have a similar problem trying to get a USB WiFi extender working on Ubuntu 10.04. 
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10716043#post10716043")

I don't have the driver. May I ask WHERE you got the driver for your wifi extender card?

Here is the wifi extender device I have:
```

$ lsusb
... 
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. 
...

```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189813&stc=1&d=1303591188[/IMG]

---

### Post by rocksockdoc on 2011-04-25
It looks like a LOT of people have been similarly burned by this Ubuntu bug:
 - [Ubuntu Karmic 32bit Realtek 8192SU driver]("http://ubuntuforums.org/showthread.php?p=10719084#post10719084")
 - [Realtek RTL8192SU driver compiling issues]("http://ubuntuforums.org/showthread.php?t=1425697")
 -[ [STAGING] realtek rtl8192su chipset based USB wireless devices fail to work    ]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17")
 **- **[Mvix Solido driver (rtl8712/8172) on 10.04]("http://ubuntuforums.org/showthread.php?t=1466185")
 - [Firmware for Realtek 8192  ]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-a-761714/page2.html")
 etc.
 [B] 
To help others, here's my summary of my particular workaround to this Ubuntu bug.
  
[/B]> **rocksockdoc said:**
> Thanks. That helped a lot to understand and  work around this (apparently known) Ubuntu bug which sidetracked me for a  day.
 
 I detailed my efforts to insert an external USB WiFi radio into my laptop in this thread:
 - [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")
 
 On my version of a pristine Ubuntu 10.04 laptop installation:
 ```
$uname -a
 ...
 Linux library 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux
 
```At first, Ubuntu would not recognize the [Amped UA600 USB WiFi radio adapter ]("http://www.ampedwireless.com/support/model/ua600.html")when it was plugged into the laptop USB port.
 
 ```

 $ ifconfig | grep wlan   
 ...
 eth0 Link encap:Ethernet  HWaddr 00:a0:c3:3a:93:38
 wlan0 Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba
 
```First, I determined the device identifier using 'list short USB":
 ```

 $ lsusb
 ...
 Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. 
 
```Then, in the /var/log/messages (dmesg | tail), I determined what driver Ubuntu was (mistakenly) looking for:
 ```

 usb 2-1: new high speed USB device using ehci_hcd and address 2
 usb 2-1: configuration #1 chosen from 1 choice
 r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned. <=== huh?
  ...
 Linux kernel driver for RTL8192 based WLAN cards
 Copyright (c) 2007-2008, Realsil Wlan
 ...
 rtl8192_proc_init_one+0x25/0x460 [r8192s_usb]
 rtl8192_usb_probe+0x148/0x191 [r8192s_usb]       **[COLOR=DarkRed]<==== NOTE: This will be useful for the modinfo [/COLOR]**command syntax!
 ...
 usbcore: registered new interface driver rtl819xU [COLOR=DarkRed]**  <=== NOTICE the "U" (Ubuntu has only the "E")**[/COLOR]
 usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
 ...
 usb 2-1: USB disconnect, address 3
 ...
 
```Placing that keyword into "module information", I could see the desired driver:
 ```

 $ modinfo r8192s_usb
 ...
 filename:       /lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
 description:    Linux driver for Realtek RTL8192 USB WiFi cards
 ...
 
```A quick look in the  /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless directory  shows an "rtl818x" directory with the following contents:
 
 ```

 $ ls -alsF /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x/*
 ...
 44 -rw-r--r--  1 root root 43176 2011-04-08 16:36 rtl8180.ko
 72 -rw-r--r--  1 root root 73640 2011-04-08 16:36 rtl8187.ko
 
```The problem appears to be that Ubuntu is looking for the following location  (which doesn't exist):
 ```

 $ ls /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin
 ...
 ls: cannot access /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin: No such file or directory
 
```The file exists (rtl8192sfw_bin); it's just in a different location on Ubuntu:
 ```

 $ ls -alsF /lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**
 ...
 /lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**:
 total 244
 -rw-r--r-- 1 root root 75984 2010-12-14 08:26 rtl8192sfw492.bin
 -rw-r--r-- 1 root root 89616 2010-12-14 08:26 rtl8192sfw74.bin
 -rw-r--r-- 1 root root 80976 2010-12-14 08:26 rtl8192sfw.bin
 
```[Post #35]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/35") and [post #36]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/36") of [this thread]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17") provided a (different sized, same-named file):
 -[ [STAGING] realtek rtl8192su chipset based USB wireless devices fail to work    ]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17")
 
 
 
 Here's what I did to obtain that differently-sized file (I guess I should call it a "driver"):
 ```

 http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
     $ gunzip rtl8192sfw.bin.gz
     $ sudo mkdir /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**
     $ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/.
 
```Finally, I was able to get Ubuntu to recognize the external WiFi radio when plugged in:
 ```

 $ ifconfig | grep wlan
 ...
 wlan0     Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba
 wlan1     Link encap:Ethernet  HWaddr f8:78:8c:a1:45:f4
 
```Now that the driver is finally working, I can get back to the original question asked in that thread:
 - [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")
 
 [IMG]http://ubuntuforums.org/attachment.php?attachmentid=189999&stc=1&d=1303756077[/IMG]

---

### Post by Sambal_Petai on 2011-07-25
hye..i experienced the same prob and can i just  copy and paste what u typed in the control panel to mine please...running 10.10

---

