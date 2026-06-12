---
title: "Ralink rt2500 USB adapter and WPA"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by TiMiD on 2010-01-22
Hi,

I have a rt2500 wireless USB adapter ( WLI-U2-KG54-AI ).

I tried to use it on 2 computers loaded with Ubuntu 9.10.
It worked well in WEP mode, but I am now trying to connect to a WPA router and the connection fails (the network manager icon keeps rolling forever).
WPA works well on those machines when using another wireless adapter (not rt2500 based).
This adapter also works well with WPA under windows.

Is this device supposed to work with Ubuntu in WPA mode :confused:

---

### Post by bkratz on 2010-01-22
> **TiMiD said:**
> Hi,

I have a rt2500 wireless USB adapter ( WLI-U2-KG54-AI ).

I tried to use it on 2 computers loaded with Ubuntu 9.10.
It worked well in WEP mode, but I am now trying to connect to a WPA router and the connection fails (the network manager icon keeps rolling forever).
WPA works well on those machines when using another wireless adapter (not rt2500 based).
This adapter also works well with WPA under windows.

Is this device supposed to work with Ubuntu in WPA mode :confused:



This may be of some use.

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

---

### Post by TiMiD on 2010-01-23
I read the link

Seems that the new drivers have problems with WPA, although the card is recommended by the FSF :
[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)

The solution would be to compile the legacy drivers, but as the support ended last year, they would probably not work with the recent kernels and it would not be very user friendly to recompile them after each kernel upgrade anyway.
cf [http://sourceforge.net/projects/rt2400/](http://sourceforge.net/projects/rt2400/)

So I guess this problem is not solvable ?

---

### Post by tragicglee on 2010-01-23
<deleted>

---

### Post by james_xxx on 2010-03-30
anyone?

---

### Post by 894yard on 2010-03-31
Running ubuntu 9.10 I have ralink with rt2500usb and can connect to the router without security but can not connect with wpa2-psk turned on. I have the exact same problem with a linksys wusb54g adapter. Both work on said router with windows OSes, though there's some kind of memory leak with the linksys in xp, neither here nor there... but the Wii, iPods, Windows machines all work well on the Belkin N router.
 
I installed the ndiswrapper with the gi and when I try to install the windows inf for the device, which I pulled from the windows machine, the gi reports that its not for my device (and shows a red x over it and won't let me try to use it)
 
I'm really new to linux as far as hardware goes, my experience is limited to accessing on terminals. If there is something I'm missing or skipping, I'd appreciate the GUIdance.
 
I have not reported the bug, as I only connected briefly to verify functionality. The OS looks nice, especially for free, but I realy need the security on the router.

---

### Post by 894yard on 2010-04-11
Okay, in case anyone is still checking this thread:  I tried the fixes offered in other threads or links from this thread, and none were successful.  I then burned the Ubuntu 8.04 LTS live disk and installed that, since I heard that these problems with WPA were new since 9.10.  That install has worked right out of the box with my WPA turned on.
 
My new problem is signal.  I used the same machine in the same position with a Windows OS and had very good connection.  Now with the same hardware running Ubuntu, the signal is poor at best.

Is there any reason that the signal would be so very poor now running Ubuntu.  I'm just looking for an explaination of fishing for anyone else who has noticed the same phenomenon since it's a bit baffling to me.  Thanks again to those who offered help in the thread as it has been a great learning experience.

---

### Post by afriza on 2010-05-29
Update: the problem still exist in 10.04 Lucid Lynx

Please update this thread if you have found a solution.

---

### Post by 894yard on 2010-05-29
I would still suggest the roll back to 8.04 LTS.  The system is very similar and requires no fiddling to make it work.  I have read in a few places that the work-arounds offered for older versions do in fact work, but they're a little more than I have time for.

Good luck.

---

### Post by MegaVolti on 2010-07-04
The problem still exists in the current version. My rt2570 card is not working with Linux and I have not found a way to use it. It works perfectly with Windows.
This only applies to WPA secured networks. Without encryption or with WEP encryption everything runs perfectly.

My web search so far has shown that for other Ralink chipsets (the rt2870) there is an error in the official driver, namely the two lines
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
are wrongly set to "=n" instead of "=y". That's why WPA doesn't wort for the rt2870 chipset and the only solution for them is to manually re-compile the driver after changing those lines.

Does the rt2570 driver maybe have the same issue? What exactly needs to be changed to fix it?

---

### Post by cheway on 2010-08-07
Don't use AES (WPA2) on your router, just use TKIP (WPA) on its own. Hope this works for you.

Matt.

EDIT: Changing it to just AES on its own will also work - it's when you have AES and TKIP on together it doesn't work.

---

