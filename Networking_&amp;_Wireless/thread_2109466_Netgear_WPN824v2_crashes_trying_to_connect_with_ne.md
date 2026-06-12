---
title: "Netgear WPN824v2 crashes trying to connect with new Quantal install"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by Quinoa Rex on 2013-01-27
This thread appears to be the same problem with no replies:
[http://ubuntuforums.org/showthread.php?t=1913478](http://ubuntuforums.org/showthread.php?t=1913478)

Every time I try to connect wirelessly to my Netgear WPN824v2 router with my new Ubuntu install, the router immediately drops all connections. It works fine with a Windows 7 install and the same wireless card, so I'm suspecting the problem is with the router itself. I've been able to connect once or twice, but I can't reproduce connecting reliably, and both times the connection dropped within a minute and the router plotzed and dropped everything.

My wireless card is a Realtek RTL8188CE 802.11b/g/n adapter. Strangely, it seems to be running on a rtl8192ce driver. I can connect via ethernet just fine. There are no firmware updates available for the router and dd-wrt doesn't support this model.

Things I've tried:
```
iwconfig wlan0 rate 2M auto
```
No change.

Tried installing rtl8188ce driver from Realtek's website -- no help. Made sure build-essential and the appropriate kernel headers were installed, no help.

It's been a week and my frustration is palpable. Any advice would be a huge help.

---

### Post by ahallubuntu on 2013-01-27
I think you're on the right track in trying to build the latest driver from Realtek for your card.  Their built-in kernel drivers are known to be problematic in 12.04 and 12.10.

I just built the latest RTL8188CE driver from Realtek without errors in 12.04 (even though I don't have this card).  People do complain about make errors, though.  You probably need to install some development packages; I was building something else recently and installed a lot of development packages which is probably why I am now able to build the driver error-free.  I could list all of the stuff I've installed but it's way more than you probably need to build this driver.  If I can figure out what you really need, I'll post it but someone else has probably figured it out.

FYI, it's common for 8188/8192 to be interchanged - I don't understand Realtek's naming methodology, but they tend to be used together.  So I'm not surprised the kernel module uses for your wireless card is rtl8192ce, and I wouldn't worry about it.  In fact, rtl8192ce is the name of the new module if you build that source code (for "RTL8188ce") like I did - there is no rtl8188ce module in the build.  (Weird - yes.)

---

### Post by Quinoa Rex on 2013-01-29
> **ahallubuntu said:**
> I think you're on the right track in trying to build the latest driver from Realtek for your card.  Their built-in kernel drivers are known to be problematic in 12.04 and 12.10.

I just built the latest RTL8188CE driver from Realtek without errors in 12.04 (even though I don't have this card).  People do complain about make errors, though.  You probably need to install some development packages; I was building something else recently and installed a lot of development packages which is probably why I am now able to build the driver error-free.  I could list all of the stuff I've installed but it's way more than you probably need to build this driver.  If I can figure out what you really need, I'll post it but someone else has probably figured it out.

FYI, it's common for 8188/8192 to be interchanged - I don't understand Realtek's naming methodology, but they tend to be used together.  So I'm not surprised the kernel module uses for your wireless card is rtl8192ce, and I wouldn't worry about it.  In fact, rtl8192ce is the name of the new module if you build that source code (for "RTL8188ce") like I did - there is no rtl8188ce module in the build.  (Weird - yes.)

Okay, I'll try it again; maybe I missed something in loading and unloading the kernel modules.

Thanks for the pointer about the interchangeability. :)

---

