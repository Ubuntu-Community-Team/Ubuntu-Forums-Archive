---
title: "No Wireless : Broadcom BCM4312 802.11b/g(rev 01)"
date: 2013-06-30
forum: Networking &amp; Wireless
---

### Post by angel mike on 2013-06-30
I have just done adual boot on my Dell Mini 1010 and cannot get a wireless connectionusing Ubantu but can with Windows XP. The fixed wire internetconnection works fine for both.


I have tried using'Additional Drivers' but get an error message – failed to install.


The systems info (when in Windows) gives :-
Dell Wireless 1397WLAN Mini Card Version 5.10.79.7
Chipset BCM4315/BCM 22062000


Putting lspci code( when in Ubantu) gives:-
Network ControllerBroadcom BCM 4312 802.11 b/g LP-PHY (rev 01)


I have downloadedthe Synaptic Package Manager but not used the code 'bcmwl-kernal-source ' as yet as there are conflicting comments aboutthis in the numerous threads - I have tried to work through these butthere does not appear to be a satisfactory solution that I can see.


Can someone give aclear method of approach on this – I do like the Ubantu concept !

---

### Post by byStanderone on 2013-06-30
...what version of ubuntu are you using, try a software update...but bheck your software sources first if the needed repos are with check marks.

---

### Post by angel mike on 2013-06-30
I have just downloaded ubantu 12.04 from the ubantu web site

---

### Post by chili555 on 2013-06-30
> Putting lspci code( when in Ubantu) gives:-
Network ControllerBroadcom BCM 4312 802.11 b/g LP-PHY (rev 01)
What does this report?```
lspci -nn -d 14e4:
```I wish all the Broadcom questions were this easy!

---

### Post by angel mike on 2013-06-30
lspci -nn -d 14e4: gives 03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)  
Thanks for replying - I hope your right about it being an easy question ! 
The ubantu version is 12.04 LTS Desktop and is upto date by the way - downloaded from ubantu.com.

---

### Post by chili555 on 2013-06-30
> **angel mike said:**
> lspci -nn -d 14e4: gives 03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)  
Thanks for replying - I hope your right about it being an easy question ! 
The ubantu version is 12.04 LTS Desktop and is upto date by the way - downloaded from ubantu.com.I've been known to be right a couple of times...

Please hook up that working ethernet and do:```
sudo apt-get install linux-headers-generic bcmwl-kernel-source
```After it completes, detach the ethernet and reboot. Then use your new wireless to give us your report.

---

### Post by angel mike on 2013-06-30
I did that but it did not work - here's the output

Reading package lists .... Done
Building dependency tree
Reading state information... Done
E:Unable to locate package bcmwl-kernal-source

The ethernet was working - I reconnected it and was able to use google.

---

### Post by chili555 on 2013-06-30
Kernel with an E, not kernal with an A. Please try again.

---

### Post by angel mike on 2013-07-01
Sorry about that - thanks for your patience ! Unfortunately still no wireless connection. Output now reads :

Reading package lists ...Done
Building dependency tree
Reading state information...Done
linux-headers-generic is already the newest version
bcmwl-kernel-source is already the newest version
0 upgrade, 0 newly installed, 0 to remove and 0 not upgraded

Regards Mike

---

### Post by chili555 on 2013-07-01
Let's probe a bit deeper:```
sudo modprobe wl
iwconfig
rfkill list all
dmesg | grep wl
```Thanks.

---

### Post by angel mike on 2013-07-01
Here is the results of the probing

[B]sudo modprobe wl 
[/B]
FATAL: Module wl not found

**iwconfig**

lo      no wireless extensions
eth0  no wireless extensions

[B]rfkill list all
[/B]
0: hci0:Bluetooth
        Soft blocked: no
        Hard blocked: no

1: compal-wifi:Wireless LAN
        Soft blocked: no
        Hard blocked: no

2:compal-bluetooth:Bluetooth
        Soft blocked: no
        Hard blocked: no

**dmesg | grep wl**

(No message)

Thanks for continuing the thread.

---

### Post by angel mike on 2013-07-01
During running the probe lines on my previous post and whilst hard wired connected the update icon 'vibrated'. Clicking on it was a list of 292 updates since the issue of this version (12.04 LTS). The last line said '292 updates have been selected 389.1MB will be downloaded. ( I previously had checked the update manager and it said everything was up to date). This version was downloaded from ubantu last week.
 I clicked on 'Install updates' box  but it did ran for only a few seconds - not enough for 389MB of data download. I clicked on 'check' box and seems to have 'hung' showing no progress on the bar after 40mins and the 'busy' icon is still going. 
How do I check that I have all the updates ?
If I have not got all 292 updates should I run all the commands posted in the replies !

---

### Post by brick2 on 2013-07-01
Hello I m a bit new to this forum but I m pretty much dealing with a same problem (Broadcom BCM4312 802.11b/g(rev 01)) and can not seam to get my wireless working.
What is wired about it is that for a while I seamed to have managed to get it to work just fine, by simply going through additional drivers, however it seamed to have stopped working properly recently, I m not sure it might have something to do with me messing around with virtual machines, because that is pretty much when a world of hurt started for me and I m not talking just about the wireless drivers.

All virtual machines have been deleted, the rest of problems resolved but this one seams to persist on end.

I followed all the steps that you have provided but nothing seams to work this is my output from the second set of commands:

iwconfig

eth0      no wireless extensions.

eth2      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

dmesg | grep wl

[    6.842119] wl: module license 'MIXED/Proprietary' taints kernel.
[    6.873129] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   12.866782] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   13.133459] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   16.569718] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   33.123180] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   50.923309] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   51.104594] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   71.090510] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  101.063360] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  141.023749] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  190.979853] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  250.924845] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  310.869322] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  370.809782] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  430.759046] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  490.703766] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  550.647547] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  610.591399] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  670.537510] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  730.480251] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  790.426390] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  850.399588] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  910.375182] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  970.349774] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1030.320884] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1090.296809] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1150.274023] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1210.246425] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1270.223494] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1330.197675] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1390.171976] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1450.146792] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1510.121509] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1570.096805] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1630.070868] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1690.045522] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1750.020975] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1809.995417] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1869.969473] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1929.944374] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1989.919417] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2049.893746] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2109.868577] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2170.249170] ERROR @wl_dev_intvar_get : error (-1)
[ 2170.249177] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 2178.970693] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2178.970837] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2198.838945] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2228.861357] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2237.044982] ERROR @wl_dev_intvar_get : error (-1)
[ 2237.044989] ERROR @wl_cfg80211_get_tx_power : error (-1)

Thank you for your time.

---

### Post by brick2 on 2013-07-01
Just to add to my previous post. I actually can install the need drivers or at least I see them as installed in additional drivers and from time to time(after like a bilion reboots) they actually function which is incredibly wired at least from my perspective.

---

### Post by angel mike on 2013-07-01
Regarding Update Manager of my previous post - I cancelled the 'check cache' and now the Update Manager shows the message ' Software on this computer is up to date'.

---

### Post by angel mike on 2013-07-01
Brick 2 - you seem to have a wl module - I do not - interesting !

---

### Post by Hadaka on 2013-07-01
@angelmike
Hi, to verify your updates are up to date
and you have the latest kernel
please do..
```
sudo apt-get update
sudo apt-get upgrade
```
thanks.

---

### Post by brick2 on 2013-07-01
Did that a while ago, tried it again to no avail. Nothing new is added, it is up to date.

---

### Post by chili555 on 2013-07-01
> **brick2 said:**
> Hello I m a bit new to this forum but I m pretty much dealing with a same problem (Broadcom BCM4312 802.11b/g(rev 01)) and can not seam to get my wireless working.
Let's verify your exact device:```
lspci -nn -d 14e4:
```

---

### Post by brick2 on 2013-07-01
lspci -nn -d 14e4:

08:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by chili555 on 2013-07-01
> **brick2 said:**
> lspci -nn -d 14e4:

08:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)With all the errors above, the first thing I'd suggest is an update and reinstall the driver. Of course, a wired ethernet connection is required:```
sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get install --reinstall bcmwl-kernel-source
```Reboot and let us check again:```
dmesg | grep wl
```

---

### Post by angel mike on 2013-07-01
Did the update/upgrade and installed bcmwl-kernel-source which seemed successful. 
Output from command after reboot

[B]dmesg | grep wl
[/B]
[26.498618] wl:module licence 'MIXED/Proprietary' taints kernel.
[26.609677] INFO @wl_cfg80211_attach : Registered CFG80211 phy

( This is not a direct copy but should be correct - not up to speed on copying/pasting from terminal yet but found a ref for it)

Thanks Mike

---

### Post by angel mike on 2013-07-02
I have a wireless connection !! Brilliant Chili555 !!! Thanks for all your effort - I might take the plunge and remove Windows XP from this Mini Dell - but first I will try a few programs on the dual boot.:)

---

### Post by brick2 on 2013-07-02
dmesg | grep wl

[   19.703441] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.774340] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  231.386605] wl: module license 'MIXED/Proprietary' taints kernel.
[  231.422614] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[  231.453079] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  232.041969] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  252.034304] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  282.022309] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)

---

### Post by brick2 on 2013-07-02
So sorry forget the last post forgot to reboot this is the output you should be looking at.


dmesg | grep wl

[   17.896127] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.933227] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   19.300875] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   19.301052] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   19.944069] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   25.367307] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   25.367494] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   47.484044] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)

---

### Post by zbeckerd on 2014-04-03
This worked for me too.  Thank you Chili555

---

