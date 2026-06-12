---
title: "Netgear WNR3500L"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by RazorThought on 2011-06-26
Hello all!  I am brand new to Ubuntu and Linux in general.  I recently purchased a WNR3500L wireless router and it works great with Windows.  However, when I boot up Ubuntu 11.04, it cannot find other wireless networks in the area.  Despite this, my internet connection speed to my computer remains unaffected...the only issue is that it cannot pick up other networks.

From searching on Google and on these forums, I've learned that most routers don't work "out of the box" with Ubuntu...NDISWrapper and additional drivers must be installed in order to make them work to their full potential.  But alas, I am a super-newb...I don't know what to do from here on to get my Netgear WNR3500L router to pick up other wireless signals.

Any and all help will be greatly appreciated.  Thanks for helping a newbie out!

---

### Post by spiky001 on 2011-06-26
I dont think you mean a Router, Do you mean a wirelesss usb device if so can you post output of lsusb.  Sorry it is a router my mistake

---

### Post by haqking on 2011-06-26
> **RazorThought said:**
> Hello all!  I am brand new to Ubuntu and Linux in general.  I recently purchased a WNR3500L wireless router and it works great with Windows.  However, when I boot up Ubuntu 11.04, it cannot find other wireless networks in the area.  Despite this, my internet connection speed to my computer remains unaffected...the only issue is that it cannot pick up other networks.

From searching on Google and on these forums, I've learned that most routers don't work "out of the box" with Ubuntu...NDISWrapper and additional drivers must be installed in order to make them work to their full potential.  But alas, I am a super-newb...I don't know what to do from here on to get my Netgear WNR3500L router to pick up other wireless signals.

Any and all help will be greatly appreciated.  Thanks for helping a newbie out!


The Netgear WNR3500L is indeed a router, however it is not meant to pick up other Wireless signals unless of course you mean as an access point/range extender i think in this case what it is pertinant is it is designed to give you one to pick up with your wifi adapater whether it be internal, external etc.

Are you asking about your machine cannot see any wireless networks other than the one your Netgear WNR3500L is giving you or your machine cannot see any at all ?

---

### Post by chili555 on 2011-06-26
Routers are devices that take the internet from your internet service provider and distribute, or route it to computers either wired directly to the router or wirelessly if, ideally, the wireless computers have the WPA password. Routers are not designed to pick up a wireless signal from other wireless devices, usually also routers, in the area.

On the other hand, the wireless card in your computer ***is*** designed to pick up a wireless signal from other wireless devices, usually also routers, in the area. In order to connect to a network, the wireless card in your computer needs to scan and see networks. Usually, users see the result in Network Manager; here is an example attached. You can see my network is GBR1; my neighbors are Dynex and MAHB.

Now my neighbor MAHB is a fair distance from my laptop; I had to step out on the porch (where I have my beer and peanuts!) to see his signal.

Are you actually referring to your wireless card in your computer?> I've learned that most routers don't work "out of the box" with Ubuntu.Most routers work perfectly with Ubuntu out of the box. Many wireless cards, I wouldn't say most, need additional drivers.

---

### Post by RazorThought on 2011-06-26
> **chili555 said:**
> 

Are you actually referring to your wireless card in your computer?Most routers work perfectly with Ubuntu out of the box. Many wireless cards, I wouldn't say most, need additional drivers.


Forgive my embarrassing newbness...I indeed meant my computer's wireless card.

Before using the Netgear WNR3500L, I used a Belkin router.  Unlike my current situation, my computer (with the Belkin router) was able to detect other wireless signals, but I was unable to connect to any of them.  My internet speed was also unbearably slow on Ubuntu...however, on Windows, it was moderately fast.  After switching to the Netgear WNR3500L, my internet speed on Ubuntu was significantly improved. but I am now unable to detect any wireless signals.

[QUOTE=haqking]

Are you asking about your machine cannot see any wireless networks other  than the one your Netgear WNR3500L is giving you or your machine cannot  see any at all ?     
[/QUOTE]

Since hooking up my Netgear WNR3500L, my machine cannot detect any wireless networks at all, including the one that the Netgear router is giving me.[QUOTE=spiky001][]("http://ubuntuforums.org/member.php?u=915355")can you post output of lsusb.

[/QUOTE]

Sure:
> 
Bus 008 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 006: ID 147a:e018 Formosa Industrial Computing, Inc. eHome Infrared Receiver
Bus 002 Device 005: ID 03f0:5c11 Hewlett-Packard PhotoSmart C4200 Printer series
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 15a9:0004 Gemtek WUBR177G
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by RazorThought on 2011-06-27
So after doing some investigating, it turns out my desktop (HP Pavilion Elite m9160f) uses a Ralink driver...a *Lite-On USB Wireless* 802.11 b/g Adaptor.  I'm not sure where to go from here, though.  Can someone help me figure out which driver to download and how to install it?  Thanks in advance.

---

### Post by chili555 on 2011-06-27
> **RazorThought said:**
> So after doing some investigating, it turns out my desktop (HP Pavilion Elite m9160f) uses a Ralink driver...a *Lite-On USB Wireless* 802.11 b/g Adaptor.  I'm not sure where to go from here, though.  Can someone help me figure out which driver to download and how to install it?  Thanks in advance.Here is your device:> Bus 002 Device 002: ID [COLOR="Red"]15a9:0004[/COLOR] Gemtek WUBR177GIt is driven by the driver rt73usb which is included by default in recent versions of Ubuntu. Let's load the module. Open a terminal and do:```
sudo modprobe rt73usb
iwconfig
```Was a wireless interface wlan0 created? Let's check for interesting kernel messages:```
dmesg | grep -e wlan -e rt73
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Please post the outcome of these commands. Some may produce no output; that means the command was executed with no errors or warnings. That's good!

---

### Post by RazorThought on 2011-06-27
Wireless is working!  Thank you so much for your help!

---

### Post by chili555 on 2011-06-27
If it's not working on reboot, post back. The module may not be loading automatically and we can fix that.

---

### Post by IrishSnow35 on 2013-02-02
Could someone help me out with the same problem? I'm using Ubuntu Studio and I tried using the same Terminal commands as above, to no avail...I don't want to have to use the Ethernet cable every time I'm using this system...can someone help?

---

### Post by chili555 on 2013-02-03
> **IrishSnow35 said:**
> Could someone help me out with the same problem? I'm using Ubuntu Studio and I tried using the same Terminal commands as above, to no avail...I don't want to have to use the Ethernet cable every time I'm using this system...can someone help?Is your device the same?```
lsusb
```

---

### Post by IrishSnow35 on 2013-02-03
> **chili555 said:**
> Is your device the same?```
lsusb
```

No, it's not...I'm sorry, I should've looked at that before.  Here's my results.

```
Bus 001 Device 002: ID 111d:0000  
Bus 001 Device 003: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. 
```

I'm not even sure that Ubuntu is even picking up my wireless card...

---

### Post by chili555 on 2013-02-04
> **IrishSnow35 said:**
> No, it's not...I'm sorry, I should've looked at that before.  Here's my results.

<snip>

I'm not even sure that Ubuntu is even picking up my wireless card...It appears it also isn't a USB card, as was the subject of this thread. Please start your own new thread and include:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

