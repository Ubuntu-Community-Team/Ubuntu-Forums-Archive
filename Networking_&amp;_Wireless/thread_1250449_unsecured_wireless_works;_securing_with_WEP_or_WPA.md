---
title: "unsecured wireless works; securing with WEP or WPA doesn't"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by summittrekker on 2009-08-26
Hi I'm new to Ubuntu and trying to set up my wireless network. I've loaded the default 9.04 Ubuntu on my old Toshiba P25-S507 computer.  This has an Atheros ar5211 wireless card installed.  My wireless card recognizes many available networks, some secured, some unsecured.  When I set my wireless router to an unsecured mode, I am able to connect.  However, when I set the wireless router to a secured mode, either WEP or WPA I'm not able to connect.  I get a menu screen asking for the password.  When I type in the password, it looks as though it is trying to connect but after about 1 minute it returns to the same menu asking for the password again.

How do I troubleshoot this?  I've seen similar but not quite the same issues in other posts and I've run many of the commands that I've seen in other posts: dmesg, ifconfig, iwconfig, lshw, etc, but I don't know what I'm looking for...?  Please help if you can.

One thing I've noticed but, I don't know if it's supposed to be this way is the logical name of my wireless card from lshw is "wmaster0".  However, when running iwconfig it says:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11ab  ESSID:"monster" 
          Mode:Managed  Frequency:5.785 GHz  Access Point: 00:23:69:BF:3E:AB  
          Bit Rate=18 Mb/s   Tx-Power=20 dBm  
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B  
          Power Management:off
          Link Quality=87/100  Signal level:-37 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

wmaster0 no wireless extensions.  The wireless name is "wlan0" instead of "wmaster0".  Could this be part of the problem?

Thanks in advance.

---

### Post by Modie101 on 2009-09-19
Hi I'm having the same problem. I have an Atheros 5007 I believe. Ok I tried and tried again to connect to my home network router which I never ever had a problem before. I installed Ubuntu on a dual boot Compaq laptop and I can not for the life of me connect to my router using WEP. I can connect to another wifi network which is unsecured I also was able to connect to my router when I disabled WEP temporarily. But with WEP enabled I am dead in the water. 

I installed Wicd and tried using the madwifi drivers and tried knetworkmanager as well but which ever I use I can not connect to a WEP enabled router.

I really hope someone can help us figure this out. 

In your case however I think that you may be configuring the wrong identifier. try selecting selecting wlan0. 

I also had a major problem because my home network was configured using Static IP, which for some brilliant reason is not well supported at all in linux.

---

### Post by blackened on 2009-09-20
> **summittrekker said:**
> ...One thing I've noticed but, I don't know if it's supposed to be this way is the logical name of my wireless card from lshw is "wmaster0"...

wmaster0 is an internal interface used by your wireless driver that, because it's still in development, is visible to iwconfig in recent kernels. It's not meant to be user-configured, and you're on the right track by jockeying wlan0. Not sure what exactly is causing your problem though.

> **Modie101 said:**
> ...Static IP, which for some brilliant reason is not well supported at all in linux.

Static IP addressing is supported perfectly by the OS itself, but, ironically, it's tools like network-manager and wicd, tools that are meant to make network configuration easier, that muck it up.

---

