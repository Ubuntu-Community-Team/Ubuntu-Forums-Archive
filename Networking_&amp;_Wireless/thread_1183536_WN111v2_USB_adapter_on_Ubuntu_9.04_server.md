---
title: "WN111v2 USB adapter on Ubuntu 9.04 server"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by aloa on 2009-06-10
In last 1 month i try to use WN111v2 (ID 0846:9001 NetGear) on my server .. i try ndiswrapper, ar9170 and otus .. no joy ..
with ndisprapper work but only on 54M , ar9170 same speed .. 

today i found in [http://forums.fedoraforum.org](http://forums.fedoraforum.org) some info that's help me to make and use WN111v2 in proper speed .. 243M .. finally n speed.. here is info from SteveGYBE that's help me .. may be help someone too..

I got a WN111v2 USB adapter with my new Netgear router and have found that the specific vendor : product ID is not included in the downloaded Otus driver code:

```
$ lsusb
Bus 002 Device 003: ID 0846:9001 NetGear, Inc. WN111(v2) RangeMax Next Wireless [Atheros AR9001U-(2)NG]
( . . . )
$ modinfo arusb_lnx
filename:       /lib/modules/2.6.27.19-170.2.35.fc10.i686/net/arusb_lnx.ko
license:        Dual BSD/GPL
description:    Atheros 802.11n Wireless LAN adapter
author:         Atheros Communications
srcversion:     9324FFEE07BB998AEC7FC4F
alias:          usb:v0846p9010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9170d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.27.19-170.2.35.fc10.i686 SMP mod_unload 686 4KSTACKS
```

This code is located in otus/OAL/Otus/Linux/zdusb.c:
```
( . . . )
/* table of devices that work with this driver */
static struct usb_device_id zd1221_ids [] = {
        { USB_DEVICE(VENDOR_ATHR, PRODUCT_AR9170) },
        { USB_DEVICE(VENDOR_DLINK, PRODUCT_DWA160A) },
        { USB_DEVICE(0x0846, 0x9010) },
        { }                                     /* Terminating entry */
};
( . . . )
```

Edit this file and replace the line
```
 { USB_DEVICE(0x0846, 0x9010) },
```
with
```
 { USB_DEVICE(0x0846, 0x9001) },
```

Then do a "make clean" followed by a "make" in your otus directory.

Once that compiles you can do a "su -c "make install"" to install your new arusb_lnx.ko kernel module.
```
$ iwconfig ath0
ath0      IEEE 802.11-MIMO  Frequency:inf GHz  Access Point: 00:00:B7:25:35:00   
          Sensitivity=0  
          Power Management:off
```

---

### Post by john stiles on 2009-07-15
To install ar9170 linux native driver ref:

[http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262](http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262)

In summary:

sudo rm -r /etc/ndiswrapper/*
sudo modprobe -rf ndiswrapper

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget [http://elektronenblitz63.de/download/Compat-Wireless_ar9170_230209.tar.gz](http://elektronenblitz63.de/download/Compat-Wireless_ar9170_230209.tar.gz)
md5sum Compat-Wireless_ar9170_230209.tar.gz

tar xvf Compat-Wireless_ar9170_230209.tar.gz
cd compat-wireless-2009-02-22_AR9170_230209

make
sudo make uninstall
sudo make install

sudo cp ar9170-*.fw /lib/firmware

Reboot. Jaunty automatically adds to network manager applet.

---

### Post by subvertbeats on 2009-07-31
John

Your instructions work fine for me - but Im getting about 30% slower speeds with this adapter than I am with the Thinkpads built in wireless-G card.

Router is a Netgear WNR2000

Any ideas?

---

### Post by john stiles on 2009-08-01
Signal strength unsolved

I'm using the same gear you are and getting 58 - 64% wn111 v2 - WNR2000. I seem to pick up a neighbour at 100% on the WN111 v2, and my laptop internal card reads my WNR2000 as 100%, so something is definitely funny with mine also. I'm still playing with the antennae and router positions/angles, but I'm in the next room to the router so it should not really be an issue.

---

### Post by john stiles on 2009-08-01
Low bit rate resolved

iwconfig reports:

wlan0     IEEE 802.11bg  ESSID:"***"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:**:**:**:**:**   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=0/100  Signal level:58/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

There is a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/384920](https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/384920)

iwconfig wlan0 rate 54M, is the maximum I can set at present. 58.5 - 300 the "n" draft speeds all fail. Still this is a significant improvement with a broadband speed test now giving 9520 Kbps.

So the 2 stage and recommended ar9170 driver only appears to be 802.11b/g on my present settings. The one stage AVM FRITZ!WLAN USB Stick N module  may overcome this if you have the time/patience to try it. In short this module is new and under development.

---

### Post by subvertbeats on 2009-08-03
John, that makes sense

lshw -C network

reports that Im on B

---

### Post by Telhma on 2009-08-09
> **john stiles said:**
> To install ar9170 linux native driver ref:

[http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262](http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262)

In summary:

sudo rm -r /etc/ndiswrapper/*
sudo modprobe -rf ndiswrapper

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget [http://elektronenblitz63.de/download/Compat-Wireless_ar9170_230209.tar.gz](http://elektronenblitz63.de/download/Compat-Wireless_ar9170_230209.tar.gz)
md5sum Compat-Wireless_ar9170_230209.tar.gz

tar xvf Compat-Wireless_ar9170_230209.tar.gz
cd compat-wireless-2009-02-22_AR9170_230209

make
sudo make uninstall
sudo make install

sudo cp ar9170-*.fw /lib/firmware

Reboot. Jaunty automatically adds to network manager applet.

NB. I have backports installed as well but am unsure if this is necessary.

Hello, I see the website you gave is german, i don't understand a word of it, do i just need to do what is standing in the summery? I have installed allready ndiswrapper.

thanks

---

### Post by john stiles on 2009-08-09
I just used the commands in the summary yes. I included the original German link as etiquette, and as there are a few more details. I found Google did a good translation.

---

### Post by john stiles on 2009-08-28
WN111 v2, the atheros ar9170 chipset, works out of the box after my upgrade to kernel 2.6.31-8 (karma alpha 4).

Note I have both ar9170-1(& 2).fw already installed as per the original installation. This may still be necessary.

Signal strength has improved to 100%
Bit rate is default to 54 Mb/s, although not yet "N".

Great news and big thanks to Otus, atheros and the linux & karmic development teams for their efforts.

---

