---
title: "yet another BCM43225 problem.."
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by thec0der on 2011-09-17
Hi there.
  Last week I brought Acer Aspire 5745G, which has a BCM43225 WiFi.
Unfortunately, it does not work.
First off all I'd like to say that every single related thread was read by me and does not help me (Every advice was tested).
And finally - I'm able to scan (see wifi's), but unable to connect to any wifi.
  OS - Ubuntu 11.04
```
uname -a
Linux xxxxxxxx 2.6.38-11-generic-pae #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 i686 i686 i386 GNU/Linux
```
```
lspci -nn 
03:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
```

```
lsmod
lib80211_crypt_tkip    17203  0 
wl                   2642531  0 
lib80211_crypt_wep     12747  0 
lib80211               14570  3 lib80211_crypt_tkip,wl,lib80211_crypt_wep
```

acer-wmi is blocked as suggest in related thread, and no changes - still see AP's, but unable to connect.
I also try with 'wl' module from ubuntu repository and with compiled by me. No changes.
I lost a week up to now in searching for solution without any luck.

Thanks,
Desislav

---

### Post by praseodym on 2011-09-17
In 11.04 you have to blacklist the module brcm80211. I also recommend WPA2-AES encryption, because of the network-manager.

---

### Post by thec0der on 2011-09-17
It is blacklisted by default, when you install STA driver.
At this moment I don't care about encryption, because I cannot connect even to open network.

---

### Post by praseodym on 2011-09-17
Did you ever install the Backport-Modules? If yes, uninstall them completely and reinstall the kernel and the driver:

```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) build-essential dkms patch fakeroot bcmwl-kernel-source
```

---

### Post by thec0der on 2011-09-18
No, I don't. I check for sure - it is not installed.
  I do reinstall of kernel and modules as you suggest, but every thing is the same as before - I see AP's, but unable to connect to any.
  It is little strange to me to see my wifi device as eth1 not as wlan0 (as always). When I use iwconfig to set ESSID and KEY for my network, It does not shown nor ESSID nor the key.

```
xxxx:~$ sudo iwconfig eth1 essid "xxxx"
xxxx:~$ sudo iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:144 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0
```

Event if I use Network-Manager, iwconfig still output the same as above.

---

### Post by thec0der on 2011-09-18
Finally I got successfully connected to wifi.
  I start connecting immediately after executing ```
sudo iwconfig eth1 rate auto
``` .
  Now I see another problem - eth1 can only see/connect from channel 1 to channel 11. Here in Europe, channels are from 1 to 13. Is there some regional settings to fix this issue?

---

### Post by praseodym on 2011-09-18
The STA driver renames the wireless interface from wlan0 to eth1. Try Wicd:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Choose **eth1** as interface name and **wext** as driver. Deactivate the NM in autostart

Edit: Is the package **iw** installed?
```
sudo apt-get install iw
sudo iw reg set DE
```
DE for Germany, use the country code of your choice. Did you update your system? There was a bug in the beginning in this driver only working on channels 1-11

---

