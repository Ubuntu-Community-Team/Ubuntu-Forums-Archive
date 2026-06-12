---
title: "Internet share for Android phone"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by randomAccess on 2011-03-30
I thought this will be as simple as in Windows 7 (connectify+virtual router). But it's not. So far I've managed to install a driver for an usb wifi dongle and now Ubuntu sees it

```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The next step was to create an AdHoc wifi network so I left-click on the network manager, chose "Create new wireless network", but I cannot see it when I scan for wifi networks via Android phone. :confused:

What am I doing wrong? Could it be that the wifi interface is down or something?

PS. when I left click on network manger, I see that under wireless networks it's written "disconnected".

---

### Post by minj on 2011-04-27
Android does not have adhoc network detection enabled. Which is nonsense but tell it to the boss.

You could try googling it (will require rooting the phone)

Or you could try to do what connectify does on linux: [Ubuntu netbook as a wireless access-point and router]("http://ubuntuforums.org/showthread.php?t=1663788")

---

### Post by thecamelcoder on 2011-04-28
You can root for phone mate, and then ir really becomes a cut down linux box. 

Heres how

[[Video] Root Your Android]("http://www.linux-geek.co.nz/2011/04/28/video-how-to-root-your-android-device-z4mod-method/")

---

### Post by chronos00 on 2011-10-16
Have anyone found an easy way to create an infrastructure-mode Acces Point with Ubuntu? (i.e. using the Network manager applet)

On the other hand, is there any easy way to configure rooted android to accept AdHoc networks? (i.e. without having to apply a path in recovery mode)

Thanks!

---

### Post by haqking on 2011-10-16
i have a google nexus running android gingerbread.

It connects to ad-hoc networks just fine without any other config.

I can create a wireless connection on my PC and connect to it in seconds with my phone, not that i do or need to.

I know reverse tethering on android does not work though

---

### Post by chronos00 on 2011-10-16
> **haqking said:**
> i have a google nexus running android gingerbread.

It connects to ad-hoc networks just fine without any other config.

I can create a wireless connection on my PC and connect to it in seconds with my phone, not that i do or need to.

I know reverse tethering on android does not work though

That is strange. I also have Gingerbread (precisely v2.3.3), on a HTC Desire. The firmware I'm using is "InsertCoin 1.05", which is an extension of the original "HTC Sense". According to your report, this is strange because you probably have almost the same Android version, and I cannot detect any adHoc networks...

Perhaps I should just upgrade my phone to make this work.

---

### Post by haqking on 2011-10-16
> **chronos00 said:**
> That is strange. I also have Gingerbread (precisely v2.3.3), on a HTC Desire. The firmware I'm using is "InsertCoin 1.05", which is an extension of the original "HTC Sense". According to your report, this is strange because you probably have almost the same Android version, and I cannot detect any adHoc networks...

Perhaps I should just upgrade my phone to make this work.

I have 2.3.6 but it worked previously in froyo anyways.

kernel 2.6.35.7-59645-g42bad32

I have just done it to retest and it takes about 10 seconds in total

---

