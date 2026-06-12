---
title: "rfkill hard block my wireless when I switch it off/on"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by Soec on 2011-06-13
Hi all,

First of all, I'm pretty new with Ubuntu, but before post it here I've  searched in a lot of forums about my problem and I found some  information, but in any case I could fix my laptop... :(

Second, sorry about my English... :)

Third, my system: My laptop is an ASUS X50R with an Atheros AR5001 wireless card. Running Ubuntu 11.04.

Fourth, my problem: Everything works ok when I launch my laptop  normally. But if I switch off my wireless connection, I can't switch it  on again because is **hardware blocked by rfkill**.

It doesn't matter the way of switching it off and on again:
- Function key + F2
- sudo ifconfig wlan0 down & sudo ifconfig wlan0 up
- switch it off in the network menu (after switch it off it says that it  is switched off by a physical switch, but it is false because my laptop  doesn't have any physical wireless switch. I think that it says this  just because it's hardware blocked).

In these cases, before switch the wireless off everything is ok:

```
mypc:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```When I switch off the wireless I have different results: Using fn+F2  Software blocked = yes, in other ways it says no. Hard block is always  off.
```
mypc:~$ rfkill list
 0: phy0: Wireless LAN
     Soft blocked: yes/no
     Hard blocked: no
```But when I try to switch it on again my heart breaks when I read:
```
mypc:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```**That's my lshw -C network**. Showing it disabled (because it's a hardware block? :confused: )
```

mypc:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:2b:9f:33
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k  driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:fa9f0000-fa9fffff
  *-network
       description: Ethernet interface
       product: L2 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: a0
       serial: 00:1d:60:a4:0a:3c
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom  ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2  driverversion=2.2.3 firmware=L2 latency=0 link=no multicast=yes  port=twisted pair
       resources: irq:40 memory:feac0000-feafffff memory:feaa0000-feabffff

```I've **tried different solutions but no one fix it:**

**1-** sudo rfkill unblock all
**2-** rmmod ath5k && modprobe ath5k
**3- **rm /dev/rfkill
**4- **sudo iwconfig wlan0 txpower auto 
**5-  **Check BIOS: wireless is always on. I think that's why when I reboot my laptop it works properly until I try to switch it off/on the wireless again. It looks like if BIOS option were turned off when I switched it off in Ubuntu... I just try to guess, because I don't really know...:smile:

I can use my wireless normally if I don't change the configuration, but precisely I changed to ubuntu to play with the different configs... 

Some ideas? Thank you.

---

### Post by Soec on 2011-06-13
One more thing, it's interesting that the wireless only work again if I shut down and start the laptop again. It doesn't happen with a reboot.... :(

---

### Post by TBABill on 2011-06-13
What happens if it shows hard blocked and you switch it to the on position, then open a terminal and ```
sudo modprobe ath5k
``` and then wait about 1 minute?

---

### Post by Soec on 2011-06-14
> **TBABill said:**
> What happens if it shows hard blocked and you switch it to the on position, then open a terminal and ```
sudo modprobe ath5k
``` and then wait about 1 minute?
Thank you for your reply, but anything happens... it is still hard blocked.

```
mipc:~$ rfkill list
**normal situation
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

**DISABLE VIA FN+F2
mipc:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

**ENABLE VIA FN+F2
mipc:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

mipc:~$ sudo modprobe ath5k
[sudo] password for mipc: 
mipc:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

In fact, once I disable the wireless I can't enable it ON again, because it's hard blocked as I said. I've tried to switch it ON with Fn+F2 but it only changes the **software block, not hardware**. 

If I try with:
```
mipc:~$ sudo ifconfig wlan0 up
[sudo] password for mipc: 
SIOCSIFFLAGS: Operation not possible due to RF-kill

```Sorry for my English, I don't know if it is correct, but when I say switch wireless ON/OFF, I mean enable/disable it with Fn+F2 or trying ifconfig wlan0 up. Because I don't have a Physical switch with ON/OFF position.

Thanks.

---

### Post by Soec on 2011-06-14
Sorry, I forgot to show the ERROR line in my dmesg:

```
[   89.388774] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by TBABill on 2011-06-14
Do you only have Ubuntu on the machine? I'm curious if the behavior is the same in Windows.

---

### Post by Soec on 2011-06-14
> **TBABill said:**
> Do you only have Ubuntu on the machine? I'm curious if the behavior is the same in Windows.
Yes, only Ubuntu. I installed it deleting Windows.

---

### Post by TBABill on 2011-06-14
Could just be a bug. Only way to know is to try another distro or Ubuntu version and see if it stays the same behavior or changes.

---

### Post by Soec on 2011-06-14
> **Soec said:**
> Yes, only Ubuntu. I installed it deleting Windows.
But a few weeks ago in windows it worked correctly.

I am still searching and trying. 

With [this]("http://ubuntuforums.org/showpost.php?p=10814969&postcount=2") (changing acer-wmi to ath5k)it doesn't work.

I am starting to be hopeless, because a lot of people have a problem that it looks the same, but all of them can fix it just unblocking rfkill, removing the acer module or switching his physical switch on :)

> **TBABill said:**
> Could just be a bug. Only way to know is to try  another distro or Ubuntu version and see if it stays the same behavior  or changes.:D
There is a non-destructive way to do this? :)

---

### Post by TBABill on 2011-06-14
Looks like you are not alone according to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478036](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478036)
 
However, your problem is a bit different because it's good till you manually set the switch to off, then can't get it to resume.
 
I had posted to sudo modprobe ath5k, but the last post in the bug report says the user was able to get theirs going on Natty by, when it happens, doing ```
sudo rmmod -f ath5k
``` and then following that with ```
sudo rfkill unblock all
``` and then ```
sudo modprobe ath5k
```

---

### Post by Soec on 2011-06-14
> **TBABill said:**
> Looks like you are not alone according to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478036](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478036)
 
However, your problem is a bit different because it's good till you manually set the switch to off, then can't get it to resume.
 
I had posted to sudo modprobe ath5k, but the last post in the bug report says the user was able to get theirs going on Natty by, when it happens, doing ```
sudo rmmod -f ath5k
``` and then following that with ```
sudo rfkill unblock all
``` and then ```
sudo modprobe ath5k
```

Wow, thank you for the link, I was searching in that place and I saw a lot of interesting threads, but I didn't find the thread that you've linked. It's almost the same problem, but the solution doesn't work. It's the same that I had tried from [here]("http://ubuntuforums.org/showpost.php?p=10814969&postcount=2") removing ath5k.

I am trying to kill the process of rfkill before remove ath5k as the first part of your link says, buy I can't find any process that looks like rfkill or something like this.

I will try posting there too.

Thank you.

---

### Post by Soec on 2011-06-15
REEDITED 

SOLVEEEEED

```
mipc:~$ modinfo ath5k
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     F4251C9C364128E69095BD1
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)
```I saw this:
```
parm:           nohwcrypt:Disable hardware encryption. (bool)

```I executed
```
mipc:~$ sudo modprobe ath5k nohwcrypt
```But it's OK now... It's strange but works, I won't ask why... :D

```
mipc:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
   ** Hard blocked: no**

```I have read in other forum that I must activate this script anyway. I did:

```
mipc:~$ sudo sh -c "echo 'options ath5k nohwcrypt' >/etc/modprobe.d/custom-wireless.conf"
```Everthing it's ok now... I expect this thread can help somebody one day... :)

Regards!
:(

---

### Post by Waklevören on 2011-07-11
Aw man.. This was -so- close to helping me out.. But I have the rt2500pci driver and that apparently doesn't have the nohwcrypt parameter. The rt73usb and rt2500usb etc does have it though, and I get online with the rt73usb stick, but as soon as I modprobe rt2500pci it goes into hwblock-mode again. 

Any ideas? I'm googling all I can, but find no equivalent to nohwcrypt for the rt2500pci :(

---

### Post by mo66 on 2011-08-28
I solved my problem of wireless being hard blocked on a toshiba netbook with realtek wifi chip.  All I did was reboot and use fuction key + F8 which is my wifi hotkey switch. During Bios Boot Screen. make it is pressed before OS takes over.

Hope this helps someone!

:guitar:

---

### Post by geeko_one on 2012-01-19
> **Soec said:**
> 
```
mipc:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
   ** Hard blocked: no**

```I have read in other forum that I must activate this script anyway. I did:

```
mipc:~$ sudo sh -c "echo 'options ath5k nohwcrypt' >/etc/modprobe.d/custom-wireless.conf"
```Everthing it's ok now... I expect this thread can help somebody one day... :)

Regards!
:(

Hi, I already in this state...and follow your next step. But my wireless tab setting was disable, and how to make my wireless search wl network automatically?
and then I checked with "lshw" :

```

  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:e8100000-e810ffff

```

---

### Post by intelligence storm on 2012-07-03
[QUOTE=Soec]                       I saw this:
     
     ```
parm:           nohwcrypt:Disable hardware encryption. (bool) 
```I executed
     
     ```
mipc:~$ sudo modprobe ath5k nohwcrypt 
```But it's OK now... It's strange but works, I won't ask why... :grin:

     ```
mipc:~$ rfkill list 0: phy0: Wireless LAN     Soft blocked: no     Hard blocked: no 
I have read in other forum that I must activate this script anyway. I did:
```     ```
mipc:~$ sudo sh -c "echo 'options ath5k nohwcrypt' >/etc/modprobe.d/custom-wireless.conf" 
```Everthing it's ok now... I expect this thread can help somebody one day... :smile:

Regards![/QUOTE]
first of all thanks alot :)....
second,sorry to bubble thread up but it's necessary hope to help.
then I'm facing same problem with fedora17 and your solution seems not to work here even I changed names as my wireless adapter is "rt73usb"
here is my "modinfo rt73usb"
```
filename:       /lib/modules/3.4.4-3.fc17.i686/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     15BB6C709D88838D196F416
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.4.4-3.fc17.i686 SMP mod_unload 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```
I don't know how to solve it exactly :(
any new tips would be useful ?
Note:I have also Ubuntu on same machine and no problem with wireless !

---

### Post by ltcarneiro on 2012-07-24
> **intelligence storm said:**
> first of all thanks alot :)....
second,sorry to bubble thread up but it's necessary hope to help.
then I'm facing same problem with fedora17 and your solution seems not to work here even I changed names as my wireless adapter is "rt73usb"
here is my "modinfo rt73usb"
```
filename:       /lib/modules/3.4.4-3.fc17.i686/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     15BB6C709D88838D196F416
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.4.4-3.fc17.i686 SMP mod_unload 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```
I don't know how to solve it exactly :(
any new tips would be useful ?
Note:I have also Ubuntu on same machine and no problem with wireless !
I have the same problem as you, with rt73usb! The only way I got wifi working is boot on ubuntu (not have this problem), turn it on then reboot on fedora 17!

This is really silly, but works. The main difference between ubuntu and fedora is, in fedora, there's a module rfkill loaded.

If anyone have a solution for this, will be great!

Sorry to post a Fedora problem on a Ubuntu forum....

---

### Post by wildmanne39 on 2012-07-24
Hi ltcarneiro, you should also post this on the fedora forum.
Thanks

---

### Post by aleixsr on 2013-01-22
In my case that solved my problem:

```
rmmod -f iwlwifi

rfkill unblock all

modprobe iwlwifi


```

Thank you very much.

---

### Post by zionkv on 2013-01-29
Does not work for me. System says "invalid argumen", when I try **sudo modprobe ath9k nohwcrypt**, but in **modinfo ath9k** I see **```
parm:           nohwcrypt:Disable hardware encryption. (int)
```**

Any ideas?
**uname -r** = 3.8.0rc4
**lspci **= 02:00.0 Device 0037 (rev 01)

---

### Post by simonenosco on 2013-11-22
sudo -i
echo "options asus_nb_wmi wapf=4" > /etc/modprobe.d/asus.conf
exit

---

### Post by crns13 on 2014-04-22
> **zionkv said:**
> Does not work for me. System says "invalid argumen", when I try **sudo modprobe ath9k nohwcrypt**, but in **modinfo ath9k** I see **```
parm:           nohwcrypt:Disable hardware encryption. (int)
```**

Any ideas?
**uname -r** = 3.8.0rc4
**lspci **= 02:00.0 Device 0037 (rev 01)

To me either. Same problem. The option nohwcrypt returns "invalid argument". This really sucks man. I have tried a solution for that at least by a couple of years. But all solutions doesn't work for me.

My rfkill list command returns:

```

0: acer-wireless: Wireless LAN
Soft blocked: no
Hard blocked: no
11: phy6: Wireless LAN
Soft blocked: no
Hard blocked: yes

```

The solution:

sudo rmmod -f ath9k
sudo rfkill unblock all
sudo modprobe ath9k


doesn't work.

The solution: add

SUSPEND_MODULES="$SUSPEND_MODULES ath9k"

to /etc/pm/config.d/unload_modules doesn't work either.

I know this is a bug, but please, is there a way to workaround this issue?

---

### Post by EkriirkE on 2014-05-12
I've also been experiencing this, though not an ubuntu user (Fedora).  A few releases ago it started, however if I put in a wifi PCMCIA card I could get back on with that.  In recent releases now after accidentally hitting the hard-switch no WiFi will ever come back on.  Except I was able to ifconfig wlan6 up (pcmcia card) without error and manually launch wpa_supplicant against it...  internal wlan0 still insisted on rf-kill.  After seeing this thread about reloading the kernel modules that seems to work or all! my internal Wifi is an intel chipset, so all I have to do is:
```
rmmod -f iwl4965
modprobe iwl4965
```

It also seems to have allowed the external PCMCIA card to function as well, despite it not being an intel chipset (only after removin+-re-inserting it)
To be this points to the cfg80211 or rfkill modules 
Thanks!

---

