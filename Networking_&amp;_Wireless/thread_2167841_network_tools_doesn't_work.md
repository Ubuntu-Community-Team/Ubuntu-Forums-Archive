---
title: "network tools doesn't work"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by iebo on 2013-08-15
hello ubuntu community  

i have installed fresh ubuntu 10.04 on my hp620 notebook more than week ago but seems not everything work well

i got alot of issues with tools like ettercap "cant find hosts " , aircrack also network manager .. internet work fine most of time even  though i had some problems :confused:.

to get wifi work i used this commands 

sudo mkdir -p /etc/Wireless/RT2860STA/ 
sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat 
sudo service network-manager restart


i did upgrade via "sudo apt-get upgrade" hoping things getting better , also tried newer kernel 2.6.32-50 but it doesn't  recognize the wifi card so i ignored 
 and allowing/blocking  modules dosent fix it

overall this notebook is really sensitive to any changes i make and always not work like i want

my recent kernal is  2.6.32-28

please guide me to create wifi interface in monitor mode probably

~$ airmon

wlan0        Ralink 2560 PCI    rt2500 (monitor mode enabled)       -- i cant see mon0

why its say ralink2560 while if  u continue reading this u will see that i have rt3090 

beside when i get into monitor i can't  see many aps in airodump just few my ap not one of them but if i connect to wifi  more access points show up


here some outputs:

hwinfo --netcard
```

UDI: /org/freedesktop/Hal/devices/pci_1814_3090
  Unique ID: y9sn.drSOnGXMLV1
  Parent ID: qTvu.8Makl3iDVc3
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "RaLink WLAN controller"
  Vendor: pci 0x1814 "RaLink"
  Device: pci 0x3090 
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x1453 
  Driver: "rt3090"
  Driver Modules: "rt3090sta"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0x98800000-0x9880ffff (rw,non-prefetchable)
  IRQ: 17 (2833841 events)
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00001814d00003090sv0000103Csd00001453bc02sc80i00"
  Driver Info #0:
    Driver Status: rt3090sta is active
    Driver Activation Cmd: "modprobe rt3090sta"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (PCI bridge)

```
 
dmesg | grep -i rt2
```

[   11.010219] Read file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed(errCode=0)!
[   11.021278] <==== rt28xx_init, Status=0
[41497.517081] rt28xx_close call RT28xxPciAsicRadioOff fail !!
[41519.412054] Read file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed(errCode=0)!
[41519.423389] <==== rt28xx_init, Status=0

```

/etc/modules

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

rt3090sta

```


sudo lshw -C network

  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 ip=192.168.1.66 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:98800000-9880ffff



/etc/network/interfaces

```
auto lo
iface lo inet loopback


```

when i edit this file my network manager stop working.

hmm hope someone help me out like chili555 and other networking geniuses

thank u

---

### Post by chili555 on 2013-08-15
Ahem. I know nothing about aircrack and I don't care to learn. You can fix this error:> Read file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed(errCode=0)!Please open a terminal and do:```
gksudo gedit /etc/Wireless/RT2860STA/RT2860STA.dat
```I suspect a new empty file will open. Add one word:```
Default
```Save and close gedit.

I can't help beyond that, I don't know about the rest.

---

### Post by iebo on 2013-08-15
thank you my friend 

 the file look better now 

dmesg | grep -i rt2

```
[   11.829917] <==== rt28xx_init, Status=0
[ 2526.993888] <==== rt28xx_init, Status=0

```


i forget to post 

dmesg | grep -i rt3
```
[   11.166382] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.223389] rt3090 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.223433] rt3090 0000:02:00.0: setting latency timer to 64
[   11.381343] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.837702] ====> rt30xx Read PowerLevelMode =  0x3.
[   11.837704] ====> rt30xx F Write 0x83 Command = 0x3.
[   23.812215] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   23.812222] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   26.816212] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   26.816217] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   29.820221] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   29.820227] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   35.832211] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   35.832215] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   38.832202] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   38.832206] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   41.832231] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   41.832237] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   44.832256] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   44.832261] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   47.832246] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   47.832251] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   50.832250] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   50.832255] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   53.836212] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   53.836219] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   56.836244] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   56.836249] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   59.836232] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   59.836236] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   77.836229] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   77.836234] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[   80.836186] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 3 
[   80.836191] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 3 
[ 2368.743825] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 62 
[ 2368.743840] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 63 
[ 2368.743850] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 64 
[ 2368.743859] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 86 
[ 2368.743869] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 82 
[ 2368.743890] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 75 
[ 2368.743902] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 66 
[ 2368.744931] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 66 
[ 2368.744944] ERROR!!!  , brt30xxBanMcuCmd = 1, Read BBP 4 
[ 2368.744953] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 4 
[ 2368.744982] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 62 
[ 2368.744992] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 63 
[ 2368.745001] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 64 
[ 2368.745010] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 86 
[ 2368.745020] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 82 
[ 2368.745029] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 75 
[ 2368.745039] ERROR!!!   brt30xxBanMcuCmd = 1. Write BBP 66 
[ 2526.994774] ====> rt30xx Read PowerLevelMode =  0x3.
[ 2526.994777] ====> rt30xx F Write 0x83 Command = 0x3.

```

---

