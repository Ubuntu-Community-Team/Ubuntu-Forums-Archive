---
title: "Adobe Flash plugin not working properly."
date: 2012-09-09
forum: Multimedia Software
---

### Post by PremiumG on 2012-09-09
Hello, fellow *buntuers! :)

I am having a highly critical issue with a regularly used plugin/application that is integrated in the stock/vanilla Chromium web browser on the latest and greatest 64-bit variation of Lubuntu that I just installed on my computer, a Dell Studio 15 with 2.1GHz Intel processor and ATI Mobility Radeon HD 3450 discreet GPU with 256MB video RAM and 3Gb total system RAM, and due to my regular necessity for this application, I am currently without a source of income as long as it does not work! :(

I am certain this web plugin runs off of Adobe Flash, but perhaps even Oracle Java as well. Regardless, The instructions that the website offers for a typical Linux installation does not work, at least, not for this stock/vanilla Chromium browser that comes preinstalled on the latest Lubuntu. :confused:

Anyway, I am deeply sorry for the essay; however, I see it crucial to provide as much information as I can, as I need this application to work so I can earn money before I can no longer pay for the internet. [-o<

But for real, here is the real issue that is really causing my loss of income. As you all may know, many OSVW's (online streaming video websites for those of you who dont know) use some form of Flash or HTML5 in order to successfully broadcast quality, and even Hi-Def!, content for users to consume at their voluntary desire for no charge what-so-ever! NO CHARGE! That's right! The site that I am highly involved with can be found at the following URL: [http://www.veetle.com](http://www.veetle.com). I highly suggest trying it out for your free video consumption needs, and is a good source of revenue if you are aware and familiar with streaming. 

Anyway, on to the real issue: after hours of plugging away at google and following various instruction, including the proprietary instructions that seem easy from the website itself, **Veetle will not stream HD content to users using Chromium web browser in Lubuntu 64-bit.**

Please help me discover a workaround to allow the plugin to work correctly in Chromium. I tried messing with Chromium's plugin folder, but it will not allow access at all!:shock:

I would greatly appreciate any useful assistance from those willing to solve this critical issue that currently exists in Lubuntu. Thank you for your support, and I like turtles.

---

### Post by marinara on 2012-09-10
did you install flash? veetle works here,  as most flash pages

---

### Post by PremiumG on 2012-09-10
Chromium has a flash plugin listed under about:plugins, checked as allowed.

---

### Post by PremiumG on 2012-09-11
Surely someone knows a workaround for Chromium.

---

### Post by marinara on 2012-09-13
you probably installed flash incorrectly.  I think the flash plugin should be installed by the ubuntu-restricted-extras package

on my system, where flash works in chrome, firefox seamonkey, and chromium, the flash plugin isn't even listed in extensions

---

### Post by TenPlus1 on 2012-09-13
[http://ubuntuforums.org/showpost.php?p=12015066&postcount=11](http://ubuntuforums.org/showpost.php?p=12015066&postcount=11)

---

### Post by PremiumG on 2012-09-14
> **TenPlus1 said:**
> [http://ubuntuforums.org/showpost.php?p=12015066&postcount=11](http://ubuntuforums.org/showpost.php?p=12015066&postcount=11)

i got this...


```
brian@brzan:~$ wget "http://dl.google.com/dl/linux/direct/google-chrome-unstable_current_i386.rpm"
--2012-09-14 02:02:03--  http://dl.google.com/dl/linux/direct/google-chrome-unstable_current_i386.rpm
Resolving dl.google.com (dl.google.com)... 74.125.134.136, 74.125.134.190, 74.125.134.91, ...
Connecting to dl.google.com (dl.google.com)|74.125.134.136|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 43655350 (42M) [application/x-redhat-package-manager]
google-chrome-unstable_current_i386.rpm: Permission denied

Cannot write to `google-chrome-unstable_current_i386.rpm' (Permission denied).
brian@brzan:~$ 
```

---

### Post by TenPlus1 on 2012-09-14
Go here and download 32-bit version for Ubuntu/Debian:

[https://www.google.com/intl/en_uk/chrome/browser/](https://www.google.com/intl/en_uk/chrome/browser/)

---

### Post by theteju on 2012-09-18
I have similar problem with my system, fresh install lubuntu 12.04 twice actually and never got flash working on any browser. I finally got rid off chrome which installed firefox by default. currently I have firefox 15.0.1 version and following is my system info if that helps....

```
drishtu@lubuntu:~$ uname -a
Linux lubuntu 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:54:40 UTC 2012 i686 athlon i386 GNU/Linux
drishtu@lubuntu:~$ dpkg -l | egrep 'flash'
ii  adobe-flash-properties-gtk           11.2.202.238-0precise1                  GTK+ control panel for Adobe Flash Player plugin version 11
ii  adobe-flashplugin                    11.2.202.238-0precise1                  Adobe Flash Player plugin version 11
drishtu@lubuntu:~$ ls /usr/lib/adobe-flashplugin/
libflashplayer.so
drishtu@lubuntu:~$ 

```

I have tried putting that libflashplayer.so file in all locations namely,

/usr/lib/mozilla/plugins
/usr/lib/firefox/plugins
home folder .mozilla/plugins etc etc with NO luck.

I do not think the computer is not powerful enough to play youtube videos because, minitube applicaiton works just fine. the system used to play videos with peppermintOS on it. 

Please help me to get the flash working. Its hard to live without youtube !!

Thanks.
-Processor-
Name		: mobile AMD Athlon(tm) XP-M (LV) 2000+
Family, model, stepping		: 6, 10, 0 (AMD Athlon XP/MP (Barton))
Vendor		: AuthenticAMD
-Configuration-
Cache Size		: 512kb
Frequency		: 398.05MHz
BogoMIPS		: 796.09
Byte Order		: Little Endian

```
 drishtu@lubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Network controller: Ralink corp. RT2500 Wireless 802.11bg (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 20)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01) 
```

---

### Post by theteju on 2012-09-18
Update : okey the problem got solved temperorily by downgrading the flash version back to 11.1

talke look at the attachment screenshot

---

### Post by pottzie on 2012-10-01
I'm going to ad that I'm having that same problems getting video to play. I've been messing with my fresh install for 2 days now, and have just gotten some video working, but not all. When I go to Youtube, some video plays while some doesn't.

 I had a heck of a time getting Lubuntu to install on this computer, I had to remove the slide show before the install would finish without freezing. I mention this because I also installed Lubuntu using the same cd on my daughter's laptop a few weeks ago, and both the installation and video worked without any problem.  
 uname -a shows that I have:
```

uname -a
Linux larry-DA236A-ABA-6420NX-NA910 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:17:36 UTC 2012 i686 athlon i386 GNU/Linux


``` and I think that may be what's causing some problems. Here's lscpu:
```

lscpu
Architecture:          i686
CPU op-mode(s):        32-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
Vendor ID:             AuthenticAMD
CPU family:            6
Model:                 8
Stepping:              0
CPU MHz:               1798.459
BogoMIPS:              3596.91
L1d cache:             64K
L1i cache:             64K
L2 cache:              256K

```

 I think the AMD cpu doesn't play well with whatever video requires. I also see that every guide says to ad software sources to the Software Center, but the Lubuntu Software Center doesn't have the "edit" tab that every guide shows for selecting and editing software sources.

---

### Post by stanwilliams on 2013-05-05
I have used Ubuntu sonce 6.06 dapper Drake now I am going back to windows, the Flash player will not work on my CPU architecture , I finally found the answer and I have to listen to artists music on website as part of my job,  makes me MAD that Adobe  did that and Firefox wont let me click to ebnable it anymore aftr going through AL the about:config  , and after I just did a clean install o 13.04 Raring and have tried for 2 more days, I Give up.

---

