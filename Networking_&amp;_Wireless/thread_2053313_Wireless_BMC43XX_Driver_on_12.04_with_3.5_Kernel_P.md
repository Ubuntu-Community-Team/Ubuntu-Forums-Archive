---
title: "Wireless BMC43XX Driver on 12.04 with 3.5 Kernel Problem"
date: 2012-09-05
forum: Networking &amp; Wireless
---

### Post by SeriousBeans on 2012-09-05
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_amd64.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-13-generic
Building for architecture x86_64
Building initial module for 3.5.0-13-generic
Error! Bad return status for module build on kernel: 3.5.0-13-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-13-generic

2012-09-05 02:21:03,848 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-05 02:21:03,849 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-09-05 02:21:03,899 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-05 02:21:06,941 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-05 02:21:06,962 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-05 02:21:06,971 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-05 02:24:54,935 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-05 02:24:55,246 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-05 02:24:55,246 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-09-05 02:24:55,298 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

Is what my log says, not too sure what to make of it. 
[https://launchpad.net/ubuntu/+source/b43-fwcutter/1:015-14/+build/3442318](https://launchpad.net/ubuntu/+source/b43-fwcutter/1:015-14/+build/3442318) I installed the latest fwcutter as well. 
When I try to activate my driver that's the error messages I get, any elp will be useful. I'm sure if I install the 3.2 kernel again I will have wifi, BUT on the 3.2 kernel my ivy bridge processor doesn't run so well with it and my computer freezes at times which is bad for compiling, so I needed it to be stable, yet 3.5 breaks wifi which is also very important, really hope someone can help.  thanks

---

### Post by chili555 on 2012-09-05
I'm confused. Well, even more confused than usual! Devices which run well with the driver b43 and the firmware which is installed by b43-fwcutter *don't* generally work with the STA driver which is installed with bcmwl-kernel-source; and vice-versa. Depending on your exact device, one is required and not the other. Let's start by identifying your exact device:```
lspci -nn | grep 0280
```

---------
For chili's reference: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)  5.100.82.**112**

---

### Post by SeriousBeans on 2012-09-05
> **chili555 said:**
> I'm confused. Well, even more confused than usual! Devices which run well with the driver b43 and the firmware which is installed by b43-fwcutter *don't* generally work with the STA driver which is installed with bcmwl-kernel-source; and vice-versa. Depending on your exact device, one is required and not the other. Let's start by identifying your exact device:```
lspci -nn | grep 0280
```

---------
For chili's reference: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)  5.100.82.**112**

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

---

### Post by chili555 on 2012-09-05
>  Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]] (rev 01) Ahhh! The famous 4727! More tears have been shed over this than I can count. My poor keyboard is drenched.

It is one of the few devices that works with *neither* b43 or wl! It is supposed to work with brcmsmac. Is it included in the 3.5.xx kernel? Let's check:```
modinfo brcmsmac | grep 4727
```If you hit pay dirt, let's load it and see what interesting messages we get:```
sudo modprobe brcmsmac
dmesg | grep brcmsmac
```Thanks; my day was starting off a bit quiet until just now!

---

### Post by SeriousBeans on 2012-09-05
> **chili555 said:**
> Ahhh! The famous 4727! More tears have been shed over this than I can count. My poor keyboard is drenched.

It is one of the few devices that works with *neither* b43 or wl! It is supposed to work with brcmsmac. Is it included in the 3.5.xx kernel? Let's check:```
modinfo brcmsmac | grep 4727
```If you hit pay dirt, let's load it and see what interesting messages we get:```
sudo modprobe brcmsmac
dmesg | grep brcmsmac
```Thanks; my day was starting off a bit quiet until just now!

I typed in all the codes and the only output I got back was ```
[ 1251.779267] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[ 1254.391558] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
```

---

### Post by chili555 on 2012-09-05
> I typed in all the codes and the only output I got back was *Nothing* from this one then?```
modinfo brcmsmac | grep 4727
```If no, then may I see:```
modinfo brcmsmac
iwconfig
```Thanks.

---

### Post by SeriousBeans on 2012-09-05
> **chili555 said:**
> *Nothing* from this one then?```
modinfo brcmsmac | grep 4727
```If no, then may I see:```
modinfo brcmsmac
iwconfig
```Thanks.

Should I be using sudo to type in the modinfo brcmsmac | grep 4727?

from the other 2 I got
```
filename:       /lib/modules/3.5.0-13-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     81190C9B86BA0E445FE8CCD
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.5.0-13-generic SMP mod_unload modversions 

-------------------------------------------------------------------------
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"GuestHome"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 26:4E:7F:8D:93:BE   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:51   Missed beacon:0

```

---

### Post by SeriousBeans on 2012-09-05
@chili555

Thanks for helping so far, I have to head to work now, if you have any solutions I'll check them out when I get home, appreciate it :).

---

### Post by chili555 on 2012-09-05
Have a great day at work!

> wlan0     IEEE 802.11bgn  [COLOR="Red"]ESSID:"GuestHome" [/COLOR] 
          Mode:Managed  Frequency:2.417 GHz  Access Point: 26:4E:7F:8D:93:BE   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="Red"]Link Quality=46/70[/COLOR]  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:51   Missed beacon:0You seem to have a wireless interface and you seem to be connected!! Yes?? Are we done here??

---

### Post by SeriousBeans on 2012-09-05
> **chili555 said:**
> Have a great day at work!

You seem to have a wireless interface and you seem to be connected!! Yes?? Are we done here??

No I'm connected via Ethernet, I used to be able to connect via WiFi but when I unplug my cable it doesn't scan for networks at all and I have no options to eon next to any. This all started after my upgrade to 3.5 kernel.

---

### Post by chili555 on 2012-09-05
I wonder if this isn't really a Network Manager problem and not a driver problem. When it's convenient, please post:```
sudo iwlist wlan0 scan
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf 
```Now aren't you late?

---

### Post by SeriousBeans on 2012-09-05
> **chili555 said:**
> I wonder if this isn't really a Network Manager problem and not a driver problem. When it's convenient, please post:```
sudo iwlist wlan0 scan
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf 
```Now aren't you late?

Lol I made it just in time to work.
I'll be home in 15minutes I'll run the command when I get home. Thanks

---

### Post by fyfe54 on 2012-09-05
I had same problem when I first installed 3.5 mainline kernel.  What I found (unfortunately, I don't remember how) was that there was an updated Broadcom driver thaqt would build in the 3.5 kernel.  
The driver was here:  [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112%2bbdcom-0ubuntu2_amd64.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112%2bbdcom-0ubuntu2_amd64.deb)

I have had no problems since.

Dell Inspiron 1545, Ubuntu 12.04, Kernel 3.6.0-030600rc4-generic
BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 
brcmwl

---

### Post by SeriousBeans on 2012-09-05
> **chili555 said:**
> I wonder if this isn't really a Network Manager problem and not a driver problem. When it's convenient, please post:```
sudo iwlist wlan0 scan
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf 
```Now aren't you late?

```
haithem@haithem:~$ sudo iwlist wlan0 scan
[sudo] password for haithem: 
wlan0     Interface doesn't support scanning : Device or resource busy
haithem@haithem:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

haithem@haithem:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
haithem@haithem:~$ 
```

---

### Post by SeriousBeans on 2012-09-05
> **fyfe54 said:**
> I had same problem when I first installed 3.5 mainline kernel.  What I found (unfortunately, I don't remember how) was that there was an updated Broadcom driver thaqt would build in the 3.5 kernel.  
The driver was here:  [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112%2bbdcom-0ubuntu2_amd64.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112%2bbdcom-0ubuntu2_amd64.deb)

I have had no problems since.

Dell Inspiron 1545, Ubuntu 12.04, Kernel 3.6.0-030600rc4-generic
BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 
brcmwl

LMAO that did it!! THANK YOU!!!!!!!!!

---

### Post by SeriousBeans on 2012-09-05
> **chili555 said:**
> I wonder if this isn't really a Network Manager problem and not a driver problem. When it's convenient, please post:```
sudo iwlist wlan0 scan
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf 
```Now aren't you late?

Thanks a lot for trying to help Chili555

Though if you do want to solve another problem I have, I keep getting errors.

[IMG]http://i50.tinypic.com/30c0wva.png[/IMG]
[IMG]http://i49.tinypic.com/1jw0b9.png[/IMG]

---

### Post by chili555 on 2012-09-06
The aptd problem will probably go away as soon as you've updated apt by all the updates Update Manager will offer. I previously had the crash about daily and now, thankfully, it's fixed! I hope the issue is not related to your 3.5.0-xx kernel. 

On the other hand I am troubled by the crash related to bcmwl-kernel-source. Isn't that what you installed that solved your wireless issue? Is it working now? What does this tell us?```
sudo dpkg -s bcmwl-kernel-source
```The -s flag asks for status. Usually, not always, the first ten or so lines tell us the problem if any.

---

