---
title: "ASUS USB-N13 issues on 11.10 [yet another]"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by CosmicCat on 2012-04-23
Hi folks,

I have poked around on many other threads for the solution to this problem, no avail. I have tried many driver variants, wacky config file commands... and I am not able to find a driver that recognizes the device. I will try to give as many details as possible.

Some things of note:
1. its a wubi install. not sure that it makes a difference
2. i have a old pci wireless card at wlan0 that just works but is slow and has a broken antenna. The USB-N13 device will be its replacement.

```

wompoo@carlos:~$ lsusb
...
Bus 001 Device 004: ID 0b05:17ab ASUSTek Computer, Inc. 
...

```
I believe that this tells us that the device is connected but not paired with a driver.

```

wompoo@carlos:~$ lsmod | grep rt
parport_pc             36962  0 
parport                46562  3 parport_pc,ppdev,lp
rtl8180                40710  0 
mac80211              462046  1 rtl8180
eeprom_93cx6           12725  1 rtl8180
cfg80211              199630  2 rtl8180,mac80211

```
Not knowing much about anything, I am going to assume that rtl8180 is the driver for the aforementioned pci card.

Trying to manually load the driver doesn't seem to work
```

wompoo@carlos:~$ dmesg | grep rt2
wompoo@carlos:~$ sudo modprobe rt2800usb 
wompoo@carlos:~$ dmesg | grep rt2
[ 9274.158731] usbcore: registered new interface driver rt2800usb
wompoo@carlos:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"sputnik"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 78:CA:39:42:DA:5D   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/100  Signal level=47/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:187  Invalid misc:88   Missed beacon:0
wompoo@carlos:~$ lsusb
...
Bus 001 Device 004: ID 0b05:17ab ASUSTek Computer, Inc. 
...

```
Like I said before, wlan0 is the old card that works but crappily.

Suggestions? I hope that I don't have to remove the old pci card until after the new one is running. I also hope that I don't have to reinstall wubi, or do a CD install.

Thanks for the help.

---

### Post by chili555 on 2012-04-23
I'm quite certain that rtl8180 is the driver for the old card. It is not correct for 0b05:17ab. If you want to use the new N13 instead, I'd blacklist the old card:```
sudo su
echo "blacklist rtl8180" >> /etc/modprobe.d/blacklist.conf
modprobe -r rtl8180
exit
```As for your new card, see post #2 and following here: [http://ubuntuforums.org/showthread.php?p=11718186](http://ubuntuforums.org/showthread.php?p=11718186)

---

### Post by CosmicCat on 2012-04-23
Thanks for the reply. If I blacklist the driver as you said, no other driver steps in to take its place.

The thread you pointed me to seemed to deal with firmware issues for a driver that is already loaded and talking to the hardware. I am not even sure which driver to modprobe once the blacklisting has taken effect. I am assuming the following:
```

sudo modprobe rt2800usb

```

However when I try this (after blacklist+reboot) I am still not seeing a device at all:

wompoo@carlos:~$ iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

Am I just trying to load the wrong driver?

---

### Post by chili555 on 2012-04-23
> The thread you pointed me to seemed to deal with firmware issues for a driver that is already loaded and talking to the hardware. Not really.> Hello,
follow the instructions for rtl8192cu V 3.3.2-3192 with DKMS.

[http://forum.ubuntuusers.de/topic/me...ion-3-3-2-3192](http://forum.ubuntuusers.de/topic/me...ion-3-3-2-3192)

modinfo 8192cu | egrep 'versi|filen|17AB'
Code:

```
filename:       /lib/modules/2.6.32-38-generic/updates/dkms/8192cu.ko
version:        v3.3.2_3192.20120103
srcversion:     5B323C24BF8EB2D52BDB625
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*
vermagic:       2.6.32-38-generic SMP mod_unload modversions 
parm:           rtw_chip_version:int

```
(you need an internet connection via cable to install the tools, headers and the driver)> Am I just trying to load the wrong driver? Yes; rt2800usb is not correct for that device.

> If I blacklist the driver as you said, no other driver steps in to take its place.It won't, until you install it as outlined. Go down to here: **rtl8192cu/s mittels DKMS**

---

### Post by CosmicCat on 2012-04-24
it worked, only when I did exactly as you said. :rolleyes:

I was intimidated by all that translated german and couldn't see the trees for the forest. In summary, here is what I did:

```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz
sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.3.23192
sudo dkms build -m rtl8192cu -v 3.3.23192
sudo dkms install -m rtl8192cu -v 3.3.23192 

```

And of course, the blacklisting you mentioned earlier.

Thanks for the help!

---

### Post by chili555 on 2012-04-24
Excellent! Your notes will help more than a few searchers, too.

Have fun!

---

### Post by reet on 2012-04-26
Thanks so much! I just bought this wireless device, and have been searching for the past few hours and trying to build and install old drivers from 2010. Compiled the rt2870sta driver and installed, but the USB device was not using it.

This work perfectly!

---

### Post by reet on 2012-04-27
Guess I spoke too soon. Even though iwconfig reports excellent signal strength and 300MB/s rate, I am limited to 54Mbps. I think this stick may be going back to the store.

---

### Post by CosmicCat on 2012-04-27
Never mind, I deleted something stupid that I just said.

---

### Post by salinmooch on 2012-04-28
This is my experience as well.  I have a Realtek chip and I tried the drivers on the CD (first time I've done in a while), from the realtek site (3.2) and then the ones linked above via DKMS (even though I'm running lucid).  For each version The stick lights up and I can connect to my N router (which generously reports 300 Mb/s or 144 Mb/s), but iperf reports a transfer of about 1.26 Mbytes/sec (12 or so Mb/sec) which is slower than than internal wireless G card.  I even tried to connect to another G router I have and the speeds were slower than my internal G.  :confused:

Help!?

Or what's a good single band chip that works with lucid ?


I'll try and test it with a windows machine to make sure the stick isn't messed before continuing.


> **reet said:**
> Guess I spoke too soon. Even though iwconfig reports excellent signal strength and 300MB/s rate, I am limited to 54Mbps. I think this stick may be going back to the store.

---

### Post by chili555 on 2012-04-28
> **salinmooch said:**
> This is my experience as well.  I have a Realtek chip and I tried the drivers on the CD (first time I've done in a while), from the realtek site (3.2) and then the ones linked above via DKMS (even though I'm running lucid).  For each version The stick lights up and I can connect to my N router (which generously reports 300 Mb/s or 144 Mb/s), but iperf reports a transfer of about 1.26 Mbytes/sec (12 or so Mb/sec) which is slower than than internal wireless G card.  I even tried to connect to another G router I have and the speeds were slower than my internal G.  :confused:

Help!?

Or what's a good single band chip that works with lucid ?


I'll try and test it with a windows machine to make sure the stick isn't messed before continuing.May I please see:```
cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```Thanks.

---

### Post by salinmooch on 2012-04-30
> **chili555 said:**
> May I please see:```
cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```Thanks.

Thanks for offering to help
Here you go:
```

$ cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
minstrel

```I found that the stick has the same issue when running on another laptop running windows - its fine at g speeds but super slow at N.  It may be an issue with my router - yet other N devices seem to do fine with the router. :confused:

---

### Post by chili555 on 2012-04-30
Please try this:```
sudo gedit /etc/modprobe.d/mac80211.conf
```Add a single line:```
options mac80211 ieee80211_default_rc_algo=minstrel_ht
```Proofread carefully, save and close gedit. Now reboot and check again:```
cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```It should now report minstrel**_ht**. Is speed improved?

---

### Post by reet on 2012-05-01
Installing Ubuntu 12.04 today. I still have the Asus N13, but also bought another USB stick which was half the price of the Asus, and works without doing anything other than plugging it in. It's called a Patriot PCBOWAU2-N.

I think my comment about the speed may have been unjustified. My problem is that I am "upgrading" from wireless-G to wireless-N, and the speed is no faster. My router runs Tomato firmware which reported the link speed to be about that of wireless-G. I am encountering the same issue with the Patriot stick, I think the problem is the lack of transmit power from a USB stick. I can only get speed faster than wireless N if I put the router in the same room as the USB device, which really defeats the whole purpose. My router is across the house from the computer, and the link according to Tomato is not good at all. There are also about a dozen other wifi networks in the area, so SNR may be a bit of an issue as well.

Anyway back to the top. I am installing Ubuntu 12.04 today, and the Asus N13 was detected without having to manually compile any kernel module or anything which is great, however I cannot connect to any network with it. The patriot stick works straight away (still).

To the above post by chili555, minstrel_ht is enabled by default in Ubuntu 12.04

---

### Post by CosmicCat on 2012-05-02
Hi folks. I downloaded a bunch of upgrades yesterday with a system restart. When the system came back up, the USB-N13 went back to its unrecognized state. Any thoughts?

```

wompoo@carlos:~$ uname -r
3.0.0-19-generic
wompoo@carlos:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 059b:047a Iomega Corp. Select Portable Hard Drive
Bus 001 Device 005: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 004 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 005 Device 002: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
wompoo@carlos:~$ sudo modinfo rtl8192cu
filename:       /lib/modules/3.0.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     6CDAA0F2DC1FD3297EBA8A6
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3359p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3358p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*
depends:        rtlwifi,mac80211,rtl8192c-common
vermagic:       3.0.0-19-generic SMP mod_unload modversions 

```

---

### Post by chili555 on 2012-05-02
> the USB-N13 went back to its unrecognized state. Any thoughts?I don't know the exact answer, but I suggest you re-run the dkms procedure as above.

---

### Post by CosmicCat on 2012-05-02
I reran the procedure. It whined because the driver was already installed. I ran this extra line:

```

sudo dkms remove -m rtl8192cu/3.3.23192 --all

```

Then followed the same procedure, and everything is working again. Thanks!

---

### Post by Killuminatii on 2012-06-19
> **CosmicCat said:**
> it worked, only when I did exactly as you said. :rolleyes:

I was intimidated by all that translated german and couldn't see the trees for the forest. In summary, here is what I did:

```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz
sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.3.23192
sudo dkms build -m rtl8192cu -v 3.3.23192
sudo dkms install -m rtl8192cu -v 3.3.23192 

```

And of course, the blacklisting you mentioned earlier.

Thanks for the help!

Wow, this solved it for me! I'm running 11.10 and I just bought this N13 adapter. Searched online for solutions, but this worked + the blacklisting. 

THANKS!

---

