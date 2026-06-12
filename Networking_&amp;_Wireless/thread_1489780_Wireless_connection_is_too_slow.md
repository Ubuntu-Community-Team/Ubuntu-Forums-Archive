---
title: "Wireless connection is too slow"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by wesamly on 2010-05-21
I am running Kubuntu 10.04 (32-bit) on a Sony VAIO VPCCW23FX, when I connected to my router through Wireless the connection is too slow and random, 3 kB - 50 kB. But when connect to the router through Ethernet cable I get the normal speed 265 kB. I read many posts but can't find solution, and already updated all packages.
 the Wireless card is:
```
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```the output of iwconfig:
```
wlan0     IEEE 802.11bgn  ESSID:"zzzzplw9"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:68:9B:0D:FE   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```the output of lsmod | grep "wlan":
```
rndis_wlan             20617  0 
rndis_host              5756  1 rndis_wlan
usbnet                 14943  3 rndis_wlan,rndis_host,cdc_ether
cfg80211              126485  4 rndis_wlan,ath9k,mac80211,ath
```

---

### Post by Mblackwell on 2010-06-12
I have this exact problem with this exact card on the VPCCW21FX (I think the only difference between our models is the Bluray drive).

So far I've attempted to install the windows driver via ndiswrapper, install backports, play with dns settings, switch to wicd, force the bit rate, and disable ipv6 at boot. I've gotten the same result every time so far: The wireless is < 1Mbit/ps with heavy speed fluctuations. It renders the computer unusable for downloading system updates (I've used ethernet for that due to the issue), or using any streaming media.

If anyone has any suggestions...

---

### Post by HrachMD on 2010-07-09
Yes,
I also have that problem on my VPCCW21FX.
Really good models, but unfortunately I can't use Internet connection with full speed.
In my case I could fix problem with connection stability and packet lost only by compilling and installing non ubuntu custom kernel - 2.6.34.1.
But I don't know how improve the speed.

---

### Post by vladimirprieto on 2010-10-08
got the same over here with VPCEB15EL

---

### Post by rafael_ebr on 2010-10-10
i'm on a VPC EB13EB with same issue (10.10 Release x86 AND x64)

try this: [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

i'm doing it yet, if works i post here.

---

### Post by hojgaard on 2010-10-14
I've had troubles like this solved by installing the linux backports for wireless.
Try it:

```
sudo apt-get install linux-backports-modules-wireless-2.6.35-22-generic && sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

---

### Post by wesamly on 2010-10-18
> **hojgaard said:**
> I've had troubles like this solved by installing the linux backports for wireless.
Try it:

```
sudo apt-get install linux-backports-modules-wireless-2.6.35-22-generic && sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

It is not working with Sony Vaio VPCCW23FX, gives the same results, remvoed ](*,)
Thanks ;)

---

### Post by CompShrink on 2010-10-23
I also have the AR9285 wireless card, and had the same problem. You could try the instructions I wrote here on fixing it: [http://ubuntuforums.org/showpost.php?p=10017274&postcount=3](http://ubuntuforums.org/showpost.php?p=10017274&postcount=3)

Good luck.

---

### Post by jarce0807 on 2010-10-23
Hi all, I got the very same issue that you all have, but i already tried all the proceses below and still got no luck, Wifi is dead slow i try this 
 
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)
 
but the link  in this command
 
sudo svn checkout [http://svn.madwifi-project.org/madwifi/trunk/](http://svn.madwifi-project.org/madwifi/trunk/) madwifi-ng
 
looks like is not available...can somebody help...i am a complete newby in ubuntu world
 
thks

---

### Post by wesamly on 2010-10-24
[@jarce0807]("http://ubuntuforums.org/member.php?u=1173813")
It's strange! I went through those instructions before, and I managed to complete all steps without issues, though it didn't change anything regarding the wireless speed.
I even ran that command now just to confirm for you, and it's working. Did you check that thread, it is long one, maybe you find someone with the same with your issue. If not try to post the output you get when you execute the command.

---

### Post by CompShrink on 2010-10-30
jarce0807, you probably don't have svn installed, it isn't installed by default. At a terminal enter:
```
sudo apt-get install subversion
```

Hope that fixes it. Good luck.

---

