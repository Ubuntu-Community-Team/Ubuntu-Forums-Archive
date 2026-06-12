---
title: "Broadcom BCM4312 card not working on Dell Vostro 1520 runninmg Jaunty"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by Bit101 on 2009-06-22
I upgraded my Ubuntu 9.04 box today with the latest updates, and now my wireless won't work (A Broadcom BCM4312). I think it might have to do with an updated kernel.

---

### Post by Bit101 on 2009-06-22
Bump

---

### Post by Ayuthia on 2009-06-22
Can you post the results of:
```
lshw -C network
lsmod|grep -e b43 -e ssb -e wl -e ndis
```It will help us see what is happening with your wireless card.

---

### Post by zostay on 2009-06-23
Similar issue, but on a Dell Mini 10.

For me, the wifi was working fine on 2.6.28-11-generic, but now the card is not working automagically anymore on 2.6.28-13-generic. Found this thread trying to resolve the issue.

lshw returned:

  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

lsmod returned nothing related to this card.

If I back up to 2.6.28-12-generic, however, lshw -C network yields:

  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:79:cb:6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

And lsmod yielded:

wl                   1489758  0
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl

I will either try a few more things on -13 or rollback to -11 again until such time as I can get my wifi working again.

---

### Post by Ayuthia on 2009-06-23
If you go into the 2.6.28-13-generic kernel, can you try the following:
```
sudo /etc/init.d/linux-restricted-modules-common start
sudo modprobe wl
```

It looks like the wl.ko module is not being loaded into /lib/modules/`uname -r`/volatile.

If that did not fix it, please post the results of:
```
ls /lib/modules/2.6.28-13-generic/volatile
```

---

### Post by ogranadino on 2009-06-23
Same problem here with 2.6.28-13 dell13.
With 2.6.28-11 no problems with boardcom wireless.

I did try an USB wifi air live turbo g and automatic loads so the problem is with boardcom.

Oscar from Chile.

---

### Post by cadcamjim on 2009-06-23
Same problem as well with same Dell.
Vostro 1520 laptop.

 2.6.28-13 dell13. DOA
With 2.6.28-11 no problems with boardcom wireless.

Hopefully somebody is able to sort this one out.
 Looks like the latest Kernel update shutdown a lot of wifi.

---

### Post by Bit101 on 2009-06-23
lshw -C network
lsmod|grep -e b43 -e ssb -e wl -e ndis

returns

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:aa:9e:bc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.8 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:3e:75:ff
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d6:a0:d0:39:3e:d2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bit@tau:~$ lsmod|grep -e b43 -e ssb -e wl -e ndis
ssb                    41220  1 b44
ndiswrapper           193436  0 
wl                   1281236  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl

```

---

### Post by zostay on 2009-06-23
I tried:

```
sudo /etc/init.d/linux-restricted-modules-common start
sudo modprobe wl
```but got:

```
% sudo /etc/init.d/linux-restricted-modules-common start
 * Preparing restricted drivers...
   ...done.
% sudo modprobe wl
FATAL: Module wl not found.
```I see the wl.ko driver in volatile though.

```
ls -l /lib/modules/2.6.28-13-generic/volatile
```yields:

```
total 2192
-rw-r--r-- 1 root root  216975 2009-06-23 13:58 ath_hal.ko
-rw-r--r-- 1 root root  124940 2009-06-23 13:58 ath_pci.ko
-rw-r--r-- 1 root root   18405 2009-06-23 13:58 ath_rate_amrr.ko
-rw-r--r-- 1 root root   25380 2009-06-23 13:58 ath_rate_minstrel.ko
-rw-r--r-- 1 root root   17528 2009-06-23 13:58 ath_rate_onoe.ko
-rw-r--r-- 1 root root   23960 2009-06-23 13:58 ath_rate_sample.ko
-rw-r--r-- 1 root root   15221 2009-06-23 13:58 wlan_acl.ko
-rw-r--r-- 1 root root   18459 2009-06-23 13:58 wlan_ccmp.ko
-rw-r--r-- 1 root root  246977 2009-06-23 13:58 wlan.ko
-rw-r--r-- 1 root root   16267 2009-06-23 13:58 wlan_scan_ap.ko
-rw-r--r-- 1 root root   26065 2009-06-23 13:58 wlan_scan_sta.ko
-rw-r--r-- 1 root root   22923 2009-06-23 13:58 wlan_tkip.ko
-rw-r--r-- 1 root root   17099 2009-06-23 13:58 wlan_wep.ko
-rw-r--r-- 1 root root   11249 2009-06-23 13:58 wlan_xauth.ko
-rw-r--r-- 1 root root 1381735 2009-06-23 13:58 wl.ko
```

---

### Post by ogranadino on 2009-06-23
In the folder
/lib/modules/2.6.28-13-generic/build/drivers/net/wireless
the driver for BC cards does exist so its weird that the wifi adapter do not load properly.
...

---

### Post by Mark2322 on 2009-06-23
This is how I got wireless driver to work on a dell inspiron600m laptop. Keep in mind I am a noobie but this may help a little. I am using the broadcom 4311 drivers so hope this helps. This was on a fresh install too.                           Okay, after some tinkering around I was able to get them to work. I will try to recite the procedure to the best of my knowledge as I didn't write it down. I first used an ethernet connection and opened the terminal and entered sudo apt-get install ndisgtk. I entered my password for the sudo command and it automatically installed ndiswrapper-utils-1.9. Then I had to blacklist native drivers by entering the following commands in the terminal: 
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb"
then entered:
sudo tee -a /etc/modprobe.d/blacklist
Okay then without closing the terminal, I opened another and entered:
sudo ndiswrapper -i ~/drivers/drivername.inf
Now I had already downloaded the drivers for my wireless card and opened
the .exe file in archive manager and extracted the .sys files and the only.inf file 
to a folder on the desktop which I named drivers
So in my case I entered sudo ndiswrapper -i ~/drivers/bcmwl5.inf
then went to windows wireless drivers in system/administration/windows wireless drivers
and chose to install new driver. I pointed it to the .inf file in the folder I named drivers
and installed. It gave me an error message saying that hardware was not present but the windows
wireless drivers window said hardware was present so I rebooted and was able to connect to my gateway
I hope this helps because I know I am not the only on with this problem. However I am using a dell
inspiron so it may not work for everyone but it should point you in the right direction if you are having trouble

---

### Post by Ayuthia on 2009-06-23
> **Bit101 said:**
> 
bit@tau:~$ lsmod|grep -e b43 -e ssb -e wl -e ndis
ssb                    41220  1 b44
ndiswrapper           193436  0 
wl                   1281236  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
[/CODE]

This is showing ndiswrapper and wl running at the same time.  Which one are you trying to use?  If you are using ndiswrapper, try the following:
```
sudo modprobe -r b44 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo modprobe b44
sudo iwlist scan
```

If you are trying to use the Broadcom STA (wl) module, try the following:
```
modprobe -r b44 ssb ndiswrapper wl
sudo modprobe wl
sudo iwlist scan
```

---

### Post by Ayuthia on 2009-06-23
organadino and cadcamjim-
If you are using the Broadcom STA option, can you check and see if the following command produces a wl.ko file:
```
ls /lib/modules/2.6.28-13-generic/volatile/wl.ko
```
If it does not, please try the following:
```
sudo /etc/init.d/linux-restricted-modules-common start
sudo depmod -a
sudo modprobe wl
sudo iwlist scan
```

---

### Post by Bit101 on 2009-06-23
> **Ayuthia said:**
> This is showing ndiswrapper and wl running at the same time.  Which one are you trying to use?  If you are using ndiswrapper, try the following:
```
sudo modprobe -r b44 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo modprobe b44
sudo iwlist scan
```

If you are trying to use the Broadcom STA (wl) module, try the following:
```
modprobe -r b44 ssb ndiswrapper wl
sudo modprobe wl
sudo iwlist scan
```

Still no wireless. the ndiswrapper one stopped eth1 from working and using wl produced
```
bit@tau:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:01:F3:21:CD
                    ESSID:"SLZG3"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-39 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

```

However, when I try to connect using wicd it never gets past "obtaining IP address"

---

### Post by jay_tee on 2009-06-23
> **Bit101 said:**
> I upgraded my Ubuntu 9.04 box today with the latest updates, and now my wireless won't work (A Broadcom BCM4312). I think it might have to do with an updated kernel.

If in the past you've had success with wifi on Jaunty with BCM4312, and find that it recently has stopped working, you may wish to check my comments in this topic:[INDENT]**[http://ubuntuforums.org/showthread.php?t=1189752](http://ubuntuforums.org/showthread.php?t=1189752)**
[/INDENT]BTW, I'm running kernel 2.6.28-13. Once I backed-out the recent hal-related updates (0.5.12~rc+git20090403-0ubuntu**_3_**), my BCM4312 began working automagically again. YMMV.

---

### Post by Bit101 on 2009-06-23
> **jay_tee said:**
> If in the past you've had success with wifi on Jaunty with BCM4312, and find that it recently has stopped working, you may wish to check my comments in this topic:[INDENT]**[http://ubuntuforums.org/showthread.php?t=1189752](http://ubuntuforums.org/showthread.php?t=1189752)**
[/INDENT]BTW, I'm running kernel 2.6.28-13. Once I backed-out the recent hal-related updates (0.5.12~rc+git20090403-0ubuntu**_3_**), my BCM4312 began working automagically again. YMMV.

If i ever find you in real life, i'm going to hug you :) It worked like a charm. Thanks man.

---

### Post by jay_tee on 2009-06-23
> **Bit101 said:**
> If i ever find you in real life, i'm going to hug you :) It worked like a charm. Thanks man.

You are quite welcome, I'm happy to have been of help ! :)

---

### Post by zostay on 2009-06-23
I ended up with a different solution. It would appear that something went awry during the install of a package or something. I ran:

```
sudo /sbin/lrm-manager
sudo modprobe wl
```The FATAL message I was getting, was apparently an indicator that that command had not been run successfully after the install (or so I guess, since I don't understand what that command does :P).

---

### Post by gtaluvit on 2009-06-23
> **zostay said:**
> I ended up with a different solution. It would appear that something went awry during the install of a package or something. I ran:

```
sudo /sbin/lrm-manager
sudo modeprobe wl
```

The FATAL message I was getting, was apparently an indicator that that command had not been run successfully after the install (or so I guess, since I don't understand what that command does :P).

This worked for me. Wireless has been sketchy for the last couple days but an ubuntu-mobile update (kernel modules) killed it today. This fixed it. THANKS!!!

---

### Post by ogranadino on 2009-06-24
I downgraded the HAL libraries (from  xxxUbuntu**3** to xxxUbuntu**1 and block the version in synaptic**) but when ubuntu loads whit kernel XXX-13 still the wifi adapter do not work.. but when I boot whit kernel XXX-11 its detected and works properly with kernel XXX-11.

**This what I get with kernel XXX-11**:

oscar@oscar-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:202  Noise level:177
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.



**this is what I get with kernel XXX-13**:

oscar@oscar-laptop:~$ iwconfig

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.


Im using a dell inspiron 13, with adapter Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
Broadcom Corporation BCM4312 802.11b/g (rev 01)

Im suing network-manager version 0.7.1~rc4.1-0Ubuntu2

---

### Post by wrench70 on 2009-06-24
> Originally Posted by zostay 
I ended up with a different solution. It would appear that something went awry during the install of a package or something. I ran:

```
Code:

sudo /sbin/lrm-manager
sudo modeprobe wl

```
The FATAL message I was getting, was apparently an indicator that that command had not been run successfully after the install (or so I guess, since I don't understand what that command does ).

This worked for me also since the 2.6.28-13 upgrade killed my wireless on my Dell mini 12 with 9.04.

---

### Post by ogranadino on 2009-07-04
Well, finally after downgrading HAL and using this 2 commands the problem is solved.

sudo /sbin/lrm-manager
sudo modprobe wl


Thanks wrench70

Regards
Oscar

---

### Post by Gladk on 2009-07-05
> **zostay said:**
> I ended up with a different solution. It would appear that something went awry during the install of a package or something. I ran:

```
sudo /sbin/lrm-manager
sudo modprobe wl
```The FATAL message I was getting, was apparently an indicator that that command had not been run successfully after the install (or so I guess, since I don't understand what that command does :P).

THANK YOU!
It helped.

Reported
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395050](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395050)

---

