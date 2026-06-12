---
title: "no wireless help! dell laptop inspiron e1505"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by dustinhxc on 2009-04-09
hello i am new to linux. i use windows vista and mac os x, now i have triple boot and use linux and am excited to use it! but cant get the wireless to work! 

i read this somewhere:
iwconfig
sudo iwlist scan
sudo lshw -C network
cat /etc/network/interfaces

and heres what i got:
ddub@ddub-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ddub@ddub-laptop:~$ sudo iwlist scan
[sudo] password for ddub: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

ddub@ddub-laptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:b8:6b:9e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:cf:89:44:53
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 46:b1:9f:8a:b7:cd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ddub@ddub-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

ddub@ddub-laptop:~$

---

### Post by Ayuthia on 2009-04-09
If you have your wired connection working, go into System->Administration->Hardware Drivers and enable the Broadcom b43 option.  It will download a firmware file that is needed to help make your wireless card work. 

If it does not work, just come back and let us know what happened and we can try some other things.  Your card is able to use the b43, Broadcom STA(wl), and ndiswrapper for wireless modules so you do have some options.  The b43 option is the best one because you have a Broadcom wired ethernet card so the other options will require you to use a workaround to make your wired and wireless cards to work.

---

### Post by dustinhxc on 2009-04-09
> **Ayuthia said:**
> If you have your wired connection working, go into System->Administration->Hardware Drivers and enable the Broadcom b43 option.  It will download a firmware file that is needed to help make your wireless card work. 

If it does not work, just come back and let us know what happened and we can try some other things.  Your card is able to use the b43, Broadcom STA(wl), and ndiswrapper for wireless modules so you do have some options.  The b43 option is the best one because you have a Broadcom wired ethernet card so the other options will require you to use a workaround to make your wired and wireless cards to work.

That worked perfect! OMG after reading all of these different posts the last few days and nothing worked. a simple enable click made it work i cant believe it. thank you!!! browsing firefox looks so nice on here!:KS;)

---

### Post by merrak on 2009-04-09
Hello! I have this same computer but the above did not work (there is no option in hardware drivers for broadcom). To make things more interesting, the wired connection does not work either. Has anyone run into this problem?

---

### Post by Ayuthia on 2009-04-09
> **merrak said:**
> Hello! I have this same computer but the above did not work (there is no option in hardware drivers for broadcom). To make things more interesting, the wired connection does not work either. Has anyone run into this problem?

Have you tried the following:
```
sudo modprobe -r b43 b44 ssb wl ndiswrapper
sudo modprobe b44
sudo ifconfig eth0 up
sudo dhclient eth0
```
Hopefully, that will get your wired card started.  If it does, please post the results of:
```
lshw -C network
lsmod|grep -e b43 -e wl
```

---

### Post by merrak on 2009-04-10
> **Ayuthia said:**
> Have you tried the following:
```
sudo modprobe -r b43 b44 ssb wl ndiswrapper
sudo modprobe b44
sudo ifconfig eth0 up
sudo dhclient eth0
```
Hopefully, that will get your wired card started.  If it does, please post the results of:
```
lshw -C network
lsmod|grep -e b43 -e wl
```

Upon "sudo dhclient eth0" I receive

```

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801

```

---

### Post by Ayuthia on 2009-04-10
If you go into the Terminal and do the following:
```
lsmod|grep b44
```does it show the b44 and ssb modules?

---

### Post by merrak on 2009-04-10
> **Ayuthia said:**
> If you go into the Terminal and do the following:
```
lsmod|grep b44
```does it show the b44 and ssb modules?

It shows both. Here is the full output:

```

b44   35984   0
ssb   40580   2 b43,b44
mii   13440   1 b44

```

---

### Post by Ayuthia on 2009-04-10
Does dmesg|grep eth show anything?  Also, have you installed the firmware for the b43 module?

---

### Post by merrak on 2009-04-10
> **Ayuthia said:**
> Does dmesg|grep eth show anything?  Also, have you installed the firmware for the b43 module?

dmesg|grep eth gives

```

[    4.792694] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:12:13:19
[    5.224242] Driver 'sr' needs updating - please use bus_type methods
[    5.232164] Driver 'sd' needs updating - please use bus_type methods
[  101.923905] b44: eth0: powering down PHY
[  136.066426] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4395.037257] b44: eth0: powering down PHY
[ 4403.266056] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:12:13:19
[ 4407.404068] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6229.577256] b44: eth0: powering down PHY
[ 6233.213019] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:12:13:19
[ 6237.119424] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

I'm pretty sure the firmware is not installed, unless 8.10 has it pre-loaded. The documentation I've found says I need to explicity get it. The problem there is that I can't download it. I do have a thumb drive, though (which is how I'm transferring the terminal output). I'm used to Gentoo's portage, so I'm not sure how to manually install something using apt-get.

Thanks for all your replies, by the way :)

---

### Post by Ayuthia on 2009-04-10
You can try this link to see if you can get the firmware installed:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

You might also check:
```
dmesg|grep b44
```It is showing that it is powering down for some reason.  The info from the b44 module might provide more information.

---

### Post by merrak on 2009-04-10
> **Ayuthia said:**
> You can try this link to see if you can get the firmware installed:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

You might also check:
```
dmesg|grep b44
```It is showing that it is powering down for some reason.  The info from the b44 module might provide more information.

This is dmesg|grep b44

```

[    4.704814] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.774097] b44.c:v2.0
[  101.923905] b44: eth0: powering down PHY
[ 4395.037257] b44: eth0: powering down PHY
[ 4395.061236] b44 0000:03:00.0: PCI INT A disabled
[ 4403.117047] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 4403.247610] b44.c:v2.0
[ 6229.577256] b44: eth0: powering down PHY
[ 6229.601222] b44 0000:03:00.0: PCI INT A disabled
[ 6233.132027] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 6233.193308] b44.c:v2.0


```

Unfortunately I'm not quite sure what it's trying to tell me. I'll try the link and see if I can get the firmware installed.

---

### Post by merrak on 2009-04-10
Looks like success! Thank you :)

Your instructions in the link you provided worked perfectly.

---

