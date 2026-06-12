---
title: "Netgear MA311"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by crash_90 on 2008-12-03
Ubuntu 8.10

I'm using a Netgear 802.11b MA311 pci card.  When i first installed Ubuntu the card worked fine.  100 or so updates later the card no longer works.  I tried booting with the previous kernel with no luck.  Does anyone know of a fix for this?

Thanks in advance.

---

### Post by pytheas22 on 2008-12-03
What is the output of these commands:
```

lshw -C Network
lspci -nn
dmesg | grep -e wlan -e eth1
```

---

### Post by crash_90 on 2008-12-03
```
  *-network:0 DISABLED    
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: wifi0
       version: 01
       serial: 00:09:5b:91:5c:8e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.3.6 latency=32 module=hostap_pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth1
       version: 30
       serial: 00:10:5a:e2:ad:5a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.0.97 latency=80 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0e:30:91:be:8e:d9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

```
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 01)
00:01.0 PCI bridge [0604]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge [8086:2561] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 MX/MX 400] [10de:0110] (rev b2)
02:09.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)
02:0c.0 Ethernet controller [0200]: 3Com Corporation 3c905B 100BaseTX [Cyclone] [10b7:9055] (rev 30)
crash@crash-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 01)
00:01.0 PCI bridge [0604]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge [8086:2561] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 MX/MX 400] [10de:0110] (rev b2)
02:09.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)
02:0c.0 Ethernet controller [0200]: 3Com Corporation 3c905B 100BaseTX [Cyclone] [10b7:9055] (rev 30)

```

```
[   15.121131] wifi0: registered netdevice wlan0
[   16.004242] udev: renamed network interface eth0 to eth1
[   28.542055] eth1:  setting half-duplex.
[  241.540615] eth1:  setting full-duplex.
[  321.972011] eth1: no IPv6 routers present
[  332.470617] eth1:  setting full-duplex.
[  343.320010] eth1: no IPv6 routers present
[  514.879562] eth1:  setting full-duplex.
[  516.306975] eth1:  setting full-duplex.
[  527.260035] eth1: no IPv6 routers present
[   15.121131] wifi0: registered netdevice wlan0
[   16.004242] udev: renamed network interface eth0 to eth1
[   28.542055] eth1:  setting half-duplex.
[  241.540615] eth1:  setting full-duplex.
[  321.972011] eth1: no IPv6 routers present
[  332.470617] eth1:  setting full-duplex.
[  343.320010] eth1: no IPv6 routers present
[  514.879562] eth1:  setting full-duplex.
[  516.306975] eth1:  setting full-duplex.
[  527.260035] eth1: no IPv6 routers present
[   15.121131] wifi0: registered netdevice wlan0
[   16.004242] udev: renamed network interface eth0 to eth1
[   28.542055] eth1:  setting half-duplex.
[  241.540615] eth1:  setting full-duplex.
[  321.972011] eth1: no IPv6 routers present
[  332.470617] eth1:  setting full-duplex.
[  343.320010] eth1: no IPv6 routers present
[  514.879562] eth1:  setting full-duplex.
[  516.306975] eth1:  setting full-duplex.
[  527.260035] eth1: no IPv6 routers present
[   15.121131] wifi0: registered netdevice wlan0
[   16.004242] udev: renamed network interface eth0 to eth1
[   28.542055] eth1:  setting half-duplex.
[  241.540615] eth1:  setting full-duplex.
[  321.972011] eth1: no IPv6 routers present
[  332.470617] eth1:  setting full-duplex.
[  343.320010] eth1: no IPv6 routers present
[  514.879562] eth1:  setting full-duplex.
[  516.306975] eth1:  setting full-duplex.
[  527.260035] eth1: no IPv6 routers present

```

---

### Post by pytheas22 on 2008-12-03
It looks like the device is still being recognized, but is 'disabled' for some reason.  Could you please post the output (in this order) also of:

```
dmesg | grep -e host -e wifi
sudo rmmod hostap_pci
sudo modprobe hostap_pci
dmesg | tail
lshw -C Network
iwconfig
```

---

### Post by pytheas22 on 2008-12-03
Also, an addendum:

If you run these commands, does the card work again:
```

sudo modprobe -r hostap hostap_cs hostap_pci orinoco_pci
sudo modprobe orinoco_pci
```

According to [this thread]("http://ubuntuforums.org/showthread.php?t=968797") (which seems to address the same problem...upgrades on Intrepid break prism-based wireless cards), this should fix it.  If it does, we can make the fix persist between reboots.

---

### Post by crash_90 on 2008-12-05
```
[   14.740316] hostap_pci 0000:02:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.740839] hostap_pci: Registered netdevice wifi0
[   14.740847] wifi0: Original COR value: 0x0
[   14.954367] wifi0: NIC: id=0x8013 v1.0.0
[   14.954673] wifi0: PRI: id=0x15 v1.0.7
[   14.958398] wifi0: STA: id=0x1f v1.3.6
[   14.969744] wifi0: defaulting to bogus WDS frame as a workaround for firmware bug in Host AP mode WDS
[   15.036901] wifi0: Intersil Prism2.5 PCI: mem=0xc4100000, irq=21
[   15.037445] wifi0: registered netdevice wlan0
[  159.247205] ADDRCONF(NETDEV_UP): wifi0: link is not ready

```

```
ERROR: Module hostap_pci is in use

```

No output for "sudo modprobe hostap_pci"

```
[  159.242004] NET: Registered protocol family 10
[  159.244934] lo: Disabled Privacy Extensions
[  159.247205] ADDRCONF(NETDEV_UP): wifi0: link is not ready
[  169.972020] eth1: no IPv6 routers present
[  182.332196] ppdev0: registered pardevice
[  182.380048] ppdev0: unregistered pardevice
[  182.748356] ppdev0: registered pardevice
[  182.849009] ppdev0: unregistered pardevice
[  187.604427] ppdev0: registered pardevice
[  187.652214] ppdev0: unregistered pardevice

```

```
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: wifi0
       version: 01
       serial: 00:09:5b:91:5c:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.3.6 latency=32 module=hostap_pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth1
       version: 30
       serial: 00:10:5a:e2:ad:5a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.0.97 latency=80 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:33:f2:1f:8b:9f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

```
lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"test"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:"test"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:5  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:231   Missed beacon:0

pan0      no wireless extensions.

```

unforutunately i can't modprobe hostap and variants because i get the following error message

```
FATAL: Module hostap is in use.
```

---

### Post by pytheas22 on 2008-12-05
Thanks for the information.

A few observations:

1. you seem to have two wireless interfaces, according to the output of 'iwconfig'.  I wonder if you can see anything with them; in other words, what happens if you type:
```

sudo iwlist scan
```

2. according to what I read via Google, the whole problem that you're experiencing seems to be caused because an update in Ubuntu 8.10 caused the system to load the hostap module to drive your card, instead of orinoco_pci--hence the hope that manually removing hostap and related modules and replacing them with orinoco_pci would solve the problem.  However, it's strange that 'modprobe -r' won't unload hostap and won't tell you which modules depend on it that are preventing it from unloading.  Do you have any better luck if you try to bring the interfaces down first, then force-unload the modules:
```

sudo ifconfig wifi0 down
sudo ifconfig wlan0 down
sudo modprobe --force -r sudo modprobe -r hostap hostap_cs hostap_pci orinoco_pci
```

If that doesn't work, what is the output of:
```

lsmod | grep hostap
```

That will tell us which modules are depending on hostap, so that we can unload them all.

---

### Post by crash_90 on 2008-12-06
Still no luck.  ```
module hostap is in use
```

here are the dependant modules

```
 lsmod | grep hostap
hostap_pci             57872  0 
hostap                114820  1 hostap_pci
ieee80211_crypt        13572  1 hostap

```

---

### Post by pytheas22 on 2008-12-07
Thanks for that.  ieee80211_crypt seems to be the problem.  Please try running these commands and post the output:
```

sudo modprobe -r hostap hostap_cs hostap_pci orinoco_pci ieee80211_crypt
sudo modprobe orinoco_pci
lshw -C Network
```

---

### Post by crash_90 on 2008-12-07
```
:~$ sudo modprobe -r hostap hostap_cs hostap_pci orinoco_pci ieee80211_crypt
FATAL: Module hostap is in use.
```

---

### Post by pytheas22 on 2008-12-07
ahhh, sorry.  It seems the version of modprobe in Ubuntu 8.10 does things in stupid ways; the 8.04 build didn't behave this way.

Anyway, please give this a try:
```

sudo rmmod ieee80211_crypt
sudo rmmod hostap_pci
sudo rmmod hostap_cs
sudo rmmod hostap
sudo rmmod orinoco_pci
sudo modprobe orinoco_pci
lshw -C Network
```

I really think it's just a matter of making it use the right module, but I don't understand why modprobe doesn't want to act normally.

Also, you might want to try enabling the backports repository (go to System>Administration>Software Sources and find the 'intrepid-backports' repository under the 'Updates' tab), then download updates.  It's possible that this bug has been fixed by now.

---

### Post by crash_90 on 2008-12-08
```
crash@crash-desktop:~$ sudo rmmod ieee80211_crypt
ERROR: Module ieee80211_crypt is in use by hostap
crash@crash-desktop:~$ sudo rmmod hostap
ERROR: Module hostap is in use by hostap_pci
crash@crash-desktop:~$ sudo rmmod hostap_pci
ERROR: Module hostap_pci is in use

```

---

### Post by pytheas22 on 2008-12-08
Sorry this is still not working.  What happens if you type:
```

sudo pccardctl ls
sudo pccardctl eject
```

---

### Post by crash_90 on 2008-12-08
Neither command produces any output.

---

### Post by pytheas22 on 2008-12-09
Sorry for the slow response.  I wanted to wait till I could really sit down and go through this all again, since it's been a while and we've made no progress.

I googled for a while and found [this thread]("http://74.125.45.132/search?q=cache:nrtahHtzrrQJ:ph.ubuntuforums.com/showthread.php%3Ft%3D964307+%22Prism+2.5+Wavelan+chipset+%22+intrepid&hl=en&ct=clnk&cd=7&gl=us&client=firefox-a"), which seems to describe your problem exactly--after applying updates to Ubuntu 8.10, wireless on Prism 2 chipsets (which include your Netgear MA311 card) stops working for some reason.

The solution (according to [this thread]("http://ubuntuforums.org/showthread.php?t=968797"), which is linked to from the one above) is supposed to be to blacklist the hostap modules.  So please run these commands:

```
echo 'blacklist hostap' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist hostap_pci' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist hostap_cs' | sudo tee -a /etc/modprobe.d/blacklist
echo orinoco | sudo tee -a /etc/modules
```

Then reboot.  Any luck?  If not, what is the output now of:
```

dmesg | grep -e oco -e wlan -e wifi -e eth1 -e hostap
lsmod | grep -e hostap -e orinoco
lshw -C Network
sudo iwlist scan
```

---

### Post by davidfg4 on 2008-12-24
Awesome! Thanks a lot pytheas22!

Those 4 commands and a reboot did the trick. :)

---

