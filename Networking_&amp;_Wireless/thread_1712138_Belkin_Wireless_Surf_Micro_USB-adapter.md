---
title: "Belkin Wireless Surf Micro USB-adapter"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by BoudewijnD on 2011-03-22
Hi,

I recently bought a [Belkin Wireless Micro USB-Adapter]("http://www.belkin.com/it/IWCatProductPage.process?Product_Id=540338"). I bought it in the Netherlands (so I don't know if it is sold abroad)/. I tried to connect it to by desktop running ubuntu 10.04 (fully updated) and on my laptop running ubuntu 10.10. But it worked on neighter version out-of-the-box. So on my desktop (10.04) i downloaded the [Realtek drivers]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true.") of the following chip set [Realtek 8192CU]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Belkin_F7D1102ed"). This gave me some singal but verry weak. The max speed was only 3Mbps. While onder Vbox (win 7) it gave 18MBps. And the singal was also lost during reboot. I look around on the form but I could not find someone else using the same micro usb adapter. Can someone tell me how to install a new and better driver for the [Belkin Wireless Micro USB-Adapter]("http://www.belkin.com/it/IWCatProductPage.process?Product_Id=540338").

More specs of the usb found only:
Belkin F7D1102ed
Belkin Surf Micro Wireless USB Adapter
Chipset: RTL8192CU
usbid: 050d:1102  

Thanx,

\BoudewijnD

ps: a pic of my config of wlan0 is included
[[IMG]http://img215.imageshack.us/img215/1053/screenshotlnb.png[/IMG]]("http://img215.imageshack.us/i/screenshotlnb.png/")

---

### Post by BoudewijnD on 2011-04-07
found a Solution on the german ubuntu forum

[http://forum.ubuntuusers.de/topic/belkin-micro-usb-adapter/#post-2717574](http://forum.ubuntuusers.de/topic/belkin-micro-usb-adapter/#post-2717574)

Be aware that during translation in  chrome the code is also translated so this will mess up the code...

---

### Post by cubefish on 2011-04-11
> **BoudewijnD said:**
> found a Solution on the german ubuntu forum

[http://forum.ubuntuusers.de/topic/belkin-micro-usb-adapter/#post-2717574](http://forum.ubuntuusers.de/topic/belkin-micro-usb-adapter/#post-2717574)

Be aware that during translation in  chrome the code is also translated so this will mess up the code...


Hi,
  thanks for the pointer.
Could you please post here the zip archive that you downloaded from the belkin driver page? the version for the rtl8192cu driver seems to have been updated (from version 2.0.1212... to version 2.0.1324...) since you/the guys on the German forum reported on it, and now when I try to compile I get the following error:

```

RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c: In function ‘_rtw_mutex_init’:
RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c:305:2: error: implicit declaration of function ‘init_MUTEX’
```So I'd like to try to compile your same version.

Thanks!

---

### Post by cubefish on 2011-05-06
Just writing to report that the driver version downloadable from the belkin website has changed to 2.0.1502, but I still can't build it on ubuntu 11.04 (I've tried on my 64bit machine as well as on a 32bit VM). The error that I get when compiling, however, has changed:

```

RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/usb_intf.c: In function ‘rtw_drv_init’:
RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1502.20110402/driver/rtl8192CU_linux_v2.0.1502.20110402/os_dep/linux/usb_intf.c:1038:23: error: ‘struct usb_device’ has no member named ‘autosuspend_delay’

```Any idea? I'd still like to try an older version of the driver source, if someone can upload it here...

---

### Post by cubefish on 2011-05-08
[edit: just to clarify, unlike BoudewijnD who started the thread, I'm trying to have this wireless card working on Ubuntu 11.04 "Natty Narwhal"]

Ok, got some news and updating the thread.

I asked directly on the German forum, and the guys there were so kind as to upload [there]("http://forum.ubuntuusers.de/post/2862310/") the 2.0.1212 version of the code. Unluckily, with this version I still get the same error that I got with the 2.0.1324 version. This, to be completely clear, is on a 8,2 (early 2011) macbook pro, WITHOUT the fancy stuff from the mactel ppa (so the fact that this is a mac shouldn't matter much, AFAIK), under the 2.6.38-9 kernel (i.e.: a more or less fresh Natty install). Note than another user on said forum [wrote]("http://forum.ubuntuusers.de/post/2862491/") that he/she was experiencing the same issue.

I experimented with a couple of other ([mainline]("https://wiki.ubuntu.com/Kernel/MainlineBuilds")) kernel versions (upon suggestion of the German forum guys) on a 32bit VM (this was because I didn't want to fiddle too much with my laptop, and because I already had a 32bit VM from earlier attempts):

[LIST]
[*]mainline 2.6.39-rc4-natty : i get yet another error (can't report it now since I'm using another machine) that prevents the driver from compiling, so no luck.
[*]**mainline 2.6.37-6-natty**: this actually **works!** it compiles and the driver seems to behave as intended. Didn't do any benchmark on performance, though.
[/LIST]
Of course, having the card to work under the 2.6.37 kernel is not extremely useful, since if I were to switch to this version I'm pretty sure I would face serious regressions on the functionality of other hardware (basically, I think I would get Maverick-y hardware support, which is definitely NOT good enough on this MBP. But this is just my guess, and it could be just wrong). So, for the time being, if I were desperate for wireless connectivity I could use a virtual machine and have it share its network connection with the host (never done that, I'm not much of an expert when it comes to VMs, but I think it should be pretty straightforward). 

This would be, of course, a clumsy, temporary solution; the true way forward would be to file a bug about this in the relevant place, and try to have it fixed. Which brings me to my last question to the forum: where should I file this bug? what should I report? does someone have any idea about this, or at least know who I should ask to?

or: any volunteer with the same problem that care to do it in my place? ;-)

cheers!

---

### Post by glards on 2011-06-11
I downloaded the last driver from belkin [3.0.1590]("ftp://WebUser:nQJ4P7b@152.104.238.19/cn/wlan/RTL8192CU_linux_v3.0.1590.20110511.zip") from May2011  and done a small patch for kernels >= 2.6.38. Those kernels do not include linux/smp_lock.h library because they removed it.

so the patch consist on modify two header files:
include/rtw_io.h
include/osdep_service.h
changing:
```

	#include <linux/smp_lock.h>

```
to:
```

#if (LINUX_VERSION_CODE < KERNEL_VERSION(2,6,38))
	#include <linux/smp_lock.h>
#endif

```

tested on kernels 2.6.38-9 2.6.39.1 and 3.0.0-0300rc2 working great on g speed( I don't have any n router to test it :()

---

### Post by cubefish on 2011-07-15
(hopefully) final update.

A couple of days ago I run a regular system update. My kernel was upgraded to 2.6.38-10, and the **linux-backports-modules-cw-2.6.39-generic**  package became available (I don't know if you actually need to enable the backports repo to get it). This package contains the driver (ok, not  really, it's a metapackage, but you get me), and **it fixes the issue without the need to do anything else**. At least on my machine, my Belkin Surf Micro N150 works smoothly.

So, to sum up: on Natty, with linux-backports-modules-cw-2.6.39-generic installed, this usb adapter works perfectly (at least for me - and I was having problems with the driver compiled from source, even when I actually managed to compile it); hopefully it should work out-of-the-box from Oneiric onwards. Yay! :p

---

### Post by leillo1975 on 2011-07-16
I installed the linux-backports-modules-cw-2.6.39-generic and now I can see mi wireless net, but , I can´t connect. I introduce the password (WPA2 Personal), and is trying to connect.

If I use another WiFi adapter I have no problems. 

The Belkin Micro USB Wifi adapter works in Windows 7 correctly.

---

### Post by leillo1975 on 2011-08-04
I tryed with Ubuntu 11.10 Alpha 3 and I have the same problem. I can´t connect. I can see my wireless, I can insert the password (WPA2), but I can´t connect...the system asks me to re-enter the password again and again...

---

### Post by spegru on 2012-02-01
Hi I'm thinking of getting one of these as they are so small.
I'm now on Mint 12 - based on Ubuntu 11.10

Does it work ok now?

thanks

---

### Post by cubefish on 2012-02-01
> **spegru said:**
> Hi I'm thinking of getting one of these as they are so small.
I'm now on Mint 12 - based on Ubuntu 11.10

Does it work ok now?

thanks

I'm not actually using it at the moment, but I took it out of the box and gave it a brief check right now: it works, at least in my case (that is: I can see and connect to a WPA2 personal network), out-of-the-box on Ubuntu 11.10 (note: I don't have linux-backports-modules-cw installed). I don't have any detailed information about signal strength etc., sorry. YMMV. I can just say that I tried surfing the web for a minute and everything looked fine.

Hope you find this useful.

---

### Post by sosaudio1 on 2012-02-01
> **cubefish said:**
> I'm not actually using it at the moment, but I took it out of the box and gave it a brief check right now: it works, at least in my case (that is: I can see and connect to a WPA2 personal network), out-of-the-box on Ubuntu 11.10 (note: I don't have linux-backports-modules-cw installed). I don't have any detailed information about signal strength etc., sorry. YMMV. I can just say that I tried surfing the web for a minute and everything looked fine.

Hope you find this useful.

On Mint 12 it does not appear to work. It is pretty much the same as 11.10 with some tweaking so any fixes that are "under the hood" for 11.10 "SHOULD" work for Mint 12. I went from Mint 12 to 11.10 to see if that would get me to the internet and so far with my n300 micro, I get the same issue. I can see my network, I just can't get it to authenticate. Someone has recommended unplugging the dongle then re-plugging it in and they said they can connect. I am at work so I cannot test this. The other option is to reboot your router....remove power for at least 30 seconds plug back in, wait, then try again.

With as many authentication errors as we are seeing, I wonder if WPA supplicant is borked somehow.

Rich

---

### Post by cubefish on 2012-02-01
> **cubefish said:**
>  my Belkin Surf Micro N150 works smoothly.


> **cubefish said:**
>  it works, at least in my case (that is: I can see and connect to a WPA2 personal network), out-of-the-box on Ubuntu 11.10 (note: I don't have linux-backports-modules-cw installed).

> **sosaudio1 said:**
>  with my n300 micro, I get the same issue. I can see my network, I just can't get it to authenticate. 

For what it's worth, I'd like to point out that we are talking about different adapters. I'm not saying that this is the reason for the difference, but it might be.

---

### Post by sosaudio1 on 2012-02-01
> **cubefish said:**
> For what it's worth, I'd like to point out that we are talking about different adapters. I'm not saying that this is the reason for the difference, but it might be.

Yeah but with the same driver and although the device ID's are different they aren't that far off...so it would stand to reason...at least on the surface that they should cover the architecture. Your's has the top speed of 150 mine goes to 300.

---

### Post by cubefish on 2012-02-02
> **sosaudio1 said:**
> Yeah but with the same driver and although the device ID's are different they aren't that far off..

True. 
Still, it would be nice to hear from somebody else who owns an N150 or an N300...

---

