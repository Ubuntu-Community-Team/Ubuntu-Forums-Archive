---
title: "Broadcom 4311 Issues (Jaunty)"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by PureLoneWolf on 2009-05-11
Hi all

I have been looking around and can't seem to find the same issue as mine.  I just installed Ubuntu Jaunty on my girlfriends laptop (Asus Pro50r) and I thought everything was going well..up until I came to use the wireless adaptor.

Where my issue seems a little different is that the Broadcom STA driver was found, activated and remains active after each reboot.  It successfully finds wireless networks correctly.  The trouble is in connecting.  My personal router (Netgear 614v6) was using WEP 128 and Ubuntu would keep coming back as if the key was incorrect.  After a while I disabled WEP and moved to just having MAC address security...this simply fails after a few attempts and tells me that wireless is disconnected.  Bear in mind that this laptop was connecting wirelessly without issue to the same router when Vista was installed.

My lcpi output is:
```

02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```

I tried to download and use WICD, but this wouldn't see any networks at all, so I went back to network-manager.

Can anyone help...I can connect her wired at my place, but at hers she has no choice but to use wireless.  

Many thanks

***EDIT***
Slight update.  I tried WICD again and something odd happened.  If I reboot, with the wired connection in and enabled...when it boots back up I can see my wireless network.  As soon as I disconnect the wire, it can no longer find any wireless networks, even following a reboot again.  This is just bizarre

---

### Post by PureLoneWolf on 2009-05-11
I have been trying various things to no avail....I tried and failed to follow the ndiswrapper how to.  WICD again

I have noticed that when I run sudo iwlist scanning, I get

eth1      Failed to read scan data : Invalid argument

I am really confused as the network-manager quite happily shows me all networks in range....  I am dangerously and disappointing near throwing it all in and installing XP...so any help would be really appreciated

**EDIT**
I just noticed when rebooting the laptop that the wireless LED is lit as expected when the laptop is booting up, but as soon as the Ubuntu login screen appears, the light switches off.  I am thinking it is a driver issue with the STA drivers...

---

### Post by amainejr on 2009-05-14
I am having similar issues.  That are repeatable, but I can't find a way to fix the problem either.  I had hardy installed and working with the STA driver, I believe.  Anyway, upgraded to Jaunty and my wireless worked, no problems.  I ran the updates, and continued working.  The following morning, the wireless just died.  It downloaded the complete Oracle 11g dbms, so I know the internet was working.  So, I did a clean installation after hours of messing with commands trying to get it working.  Viola, it worked premium on the initial installation.  Again, I ran the update manager, went to bed and it won't connect anymore.  I repeated it one more time, and still the same results.  I am lost.

I am using the Broadcom 4311 14:e4 version with the wl (STA) driver by default.  After the updates ran, it apparently done something to the driver.  

```
sudo iwlist scan
``` 

That comes up with the list of all of the available networks.  They are shown in network manager, but when I go to connect, the daemon log shows something along the lines of 'Failure to Associate request with driver'.  What else do I need to do or could it be?

---

### Post by Peter09 on 2009-05-14
Does this bug reflect your problems

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291220](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291220)

---

### Post by superprash2003 on 2009-05-14
try this , just for testing, disable MAC security, do not use WEP,WPA etc leave it open , and then try connecting , does it work??

---

### Post by PureLoneWolf on 2009-05-14
I personally tried to disable all router security but it didn't work.  

It is definitely a driver thing though.  I came closest when I tried Mandriva.  The driver they are shipping doesn't turn off the wireless light and I even made a connection to the router, but it wouldn't function with DHCP.  

In the end I opted to buy a different USB Wireless Card which worked immediately and natively.

---

