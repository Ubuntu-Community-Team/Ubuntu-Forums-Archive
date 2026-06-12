---
title: "AE1000 Wireless adapter won't work in Ubuntu 12.04 Precise Pangolin (32 Bit)"
date: 2012-05-06
forum: Networking &amp; Wireless
---

### Post by Turalyon on 2012-05-06
Hello everyone,

I know I posted this AFTER I solved it, so if it's in the wrong place send me a whisper and I'll fix it.

Here is a fix for the Wireless AE1000 adapter not working in Ubuntu 12.04 (32 Bit). You will need to be connected to the Internet with a wired connection while you do this, and your adapter will need to be plugged in to your USB port.

This also works in Ubuntu 11.10 (32 Bit)

Here are the commands you will need to copy and paste into a terminal, it will ask you for your password.

```
sudo apt-get install build-essential linux-headers-generic
``````
wget [http://blog.up-link.ro/files/2010_0915_RT3572_Linux_STA_v2.4.0.2.zip](http://blog.up-link.ro/files/2010_0915_RT3572_Linux_STA_v2.4.0.2.zip)
``````
unzip 2010_0915_RT3572_Linux_STA_v2.4.0.2.zip
``````
cd 2010_0915_RT3572_Linux_STA_v2.4.0.2/
``````
make
``````
sudo make install
``````
sudo modprobe rt3572sta
```

You can also click this link and it will bring you to the website I found this information on.

[http://blog.up-link.ro/ubuntu-how-to-build-and-install-linksys-ae1000-wireless-n-linux-driver-on-ubuntu-11-10/](http://blog.up-link.ro/ubuntu-how-to-build-and-install-linksys-ae1000-wireless-n-linux-driver-on-ubuntu-11-10/)

---

### Post by jawilljr on 2012-05-06
I also have a AE1000 working in Precise...but I am using the official RT2800USB drivers.

lsusb:

```
Bus 002 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT3572]
```

Definitely AE1000

lsmod | grep rt2:

```
rt2800usb              22615  0 
rt2800lib              58379  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20618  1 rt2800usb
rt2x00lib              54769  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              523736  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              209911  2 rt2x00lib,mac80211
compat                 13447  6 rfcomm,bnep,bluetooth,rt2800usb,mac80211,cfg80211
```

iwconfig:

```
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"KJAWJR"  
          Mode:Managed  [color=red]Frequency:5.18 GHz[/color]  Access Point: C0:C1:C0:38:4F:32   
          [color=red]Bit Rate=144.4 Mb/s[/color]   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:73   Missed beacon:0

eth0      no wireless extensions.
```

Notice in red? Both 5Ghz and wireless N.

All I did was compile and install the latest compat-wireless, which as of this writing is compat-wireless-3.4-rc3-1. I also turned off power managment.

The above will also work in Oneiric...It will also work in Lucid and Maverick, you just have to update the firmware in those.

Jerry

---

### Post by gustrix on 2012-05-11
Hi Jerry,

Thanks for the tip, worked perfectly for me.

Mattias

---

### Post by jawilljr on 2012-05-11
> **gustrix said:**
> Hi Jerry,

Thanks for the tip, worked perfectly for me.

Mattias


No problem. Right now I am posting this using an AE1000 in Lucid, using the same compat-wireless-3.4-rc3-1 version.

lsb_release -a:

```
kjawhtpc@kjawhtpc:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid
```

uname -r:

```
kjawhtpc@kjawhtpc:~$ uname -r
2.6.32-41-generic
```

modinfo rt2800usb | grep srcversion:

```
srcversion:     CE7360EF4693E01F38DEB3D
```

The iwconfig is pretty the same as I get with Precise... 5 Ghz and wireless N. The main difference is I got the latest rt2870.bin firmware [from here](http://git.kernel.org/?p=linux/kernel/git/firmware/linux-firmware.git;a=tree;h=5c10f3d6a5c76dca943ae68926b602bd0a1eae35;hb=5c10f3d6a5c76dca943ae68926b602bd0a1eae35). Which was updated with [this kernel commit](http://git.kernel.org/?p=linux/kernel/git/firmware/linux-firmware.git;a=commit;h=5c10f3d6a5c76dca943ae68926b602bd0a1eae35)

Oneiric and Precise comes with the above by default...Lucid and Maverick needs the above firmware..

Also with all the above... turn off Power management... I just wish serialmonkey would have implemented [this patch](http://rt2x00.serialmonkey.com/pipermail/users_rt2x00.serialmonkey.com/2011-January/003017.html), at least till they fixed the power management issues. But they didn't.

Jerry

---

### Post by abarbaccia on 2012-05-25
Hi Jerry
I recently updated to 12.04 and was using the rt3572sta drivers and am trying to switch to the rt2800usb using compat-wireless as you suggested. I have the modules loaded and things seem stable. If I set the region to US, I can see my 5ghz network and connect to it. Problem I'm having is that the speeds never go above 30mbps, so I'm lacking n support.  

Can you provide any advice? 

I'm running firmware version 29.

---

