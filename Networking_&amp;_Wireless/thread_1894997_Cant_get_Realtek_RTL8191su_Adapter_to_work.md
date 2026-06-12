---
title: "Cant get Realtek RTL8191su Adapter to work"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by ianlone81 on 2011-12-13
[FONT=Calibri]1.       [/FONT]Machine Name brand and model :Laptop Acer Aspire 4743Z Windows7 64-bit Home Basic Edition


  Im using backtrack5 in my VMware Player version 3.1.3 build-324285
   
  [FONT=Calibri]2.       [/FONT]Wireless Brand,Model & wireless chipset : 
  Atheros ARB5B97 wireless network adapter
   
  Im using Realtek  RTL8191su adapter in which it cannot detect wireless in the VMware player.
   
  Here's the codes I entered:
  $lsusb  -     Bus: 001
                    Device :002
                    ID Obda: 8172u
   
  [FONT=Calibri]3.       [/FONT]Check interface – 
  $iwconfig wlan1 
  unassociated nickname : “rtl_wifi”
  Mode: auto Access point: not associated  sensitivity:0/0
  Retry: off RTS thr: off   fragment thr: off
  Encryption key: of
  Link quality:0 signal level:0 noise level:0
  Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
  Tx excessive retries:0 invalid misc: 0 missed beacon
   
  $if wconfig
  Eth0 link encap: Ethernet
           Int addr:  I see ip add here
          Up broadcast running multicast
          Some packets & zero’s down & errors. Etc.
   
  L0 link encap: local loopback
       Net addr: Ip add again
       Up loopback running


  [FONT=Calibri]4.       [/FONT]$Lshw –C network
  *network disabled
  Description: wireless interface
  Physical ID:2
  Bus info: usb@1:1
  Logical name: wlan1
  Configuration:broadcast:yes,driver:r8172u,multicas  t:yes,wireless:unassociated
  [FONT=Calibri]5.       [/FONT]Scan for network;
  $iwlist scan
  Lo : interface doesn’t support scanning
  Eth0:interface doesn’t support scanning
  Wlan1: no scan result
   
  [FONT=Calibri]6.       [/FONT]Ubunto version.
  Ubunto 10.04.2 LTS


  [FONT=Calibri]7.       [/FONT]Kernel architecture
  2.6.38.i686
   
  Hope you can help me solve this problem.Please state any more code and result  to be posted if any.

---

### Post by pytheas22 on 2011-12-14
Were the commands whose output you posted run inside Ubuntu, or inside your backtrack virtual machine?  We would need to see them from both environments.  In addition, the output of the command "lsusb" in both Ubuntu and backtrack would be helpful.  Finally, if possible please just copy and paste the output; above it looks like you tried to copy it over by hand and there are a lot of examples of what look like typos, which are confusing.

Also, I'm wondering why you want to do this.  You should be able to get your virtual machine connected to the Internet without passing through the physical wireless card, and anything you can do with the wireless card under backtrack you should also be able to do in Ubuntu itself.  Unless you're trying to do something specific you may be going to a lot of trouble for nothing.

---

### Post by ianlone81 on 2011-12-14
its inside backtrack.the adapter seems not detecting the wireless signal. 

for lsusb command here's the output. 
> Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub for iwconfig command: 
> lo        no wireless extensions.  
eth0      no wireless extensions. 
 wlan1     unassociated  Nickname:"rtl_wifi"           Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0             Retry:off   RTS thr:off   Fragment thr:off           Encryption key:off           Power Management:off           Link Quality:0  Signal level:0  Noise level:0           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 for $lshw -c network command: 
 > *-network                       description: Ethernet interface        product: 79c970 [PCnet32 LANCE]        vendor: Advanced Micro Devices [AMD]        physical id: 1        bus info: pci@0000:02:01.0        logical name: eth0        version: 10        serial: 00:0c:29:6a:b3:50        width: 32 bits        clock: 33MHz        capabilities: bus_master rom ethernet physical logical        configuration: broadcast=yes driver=pcnet32 driverversion=1.35 ip=192.168.61.128 latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes        resources: irq:19 ioport:2000(size=128) memory:dc400000-dc40ffff   *-network DISABLED        description: Wireless interface        physical id: 2        bus info: usb@1:1        logical name: wlan1        serial: 78:44:76:86:1b:00        capabilities: ethernet physical wireless        configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated hope this help a bit for clarification.

---

### Post by pytheas22 on 2011-12-14
What is the output inside backtrack of:
```

iwlist scan
whoami
```

run as root?

---

### Post by ianlone81 on 2011-12-15
yes. run in root. 

$iwlist scan

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     No scan results


$whoami.

> root

---

### Post by pytheas22 on 2011-12-16
From the output you've posted it looks like everything should be working.  The wireless card simply doesn't detect any networks.  That could be because of low signal strength, the wrong mode (e.g., your network is on 802.11n mode but the wireless card is in 802.11g, or vice-versa) or something else.  Unfortunately this is an issue on backtrack's end, not Ubuntu's, and I don't know too much about backtrack.  You could try compiling the driver for your card from source again but I'm not even sure how to do that on backtrack.

If you told me what you were actually trying to do that might make it easier to solve your ultimate goal.  If you want to do aircrack or something like that, you're probably going to more trouble than you need to because you could just run that stuff from inside Ubuntu, without using a virtual machine.

---

### Post by ianlone81 on 2011-12-18
sorry for late reply. yeah your right i want to crack some wifi passwords to connect. it happens that my friends used this kind of device and succesfully cracked passwords. my works travel a lot and as much as possible internet is needed. if your willing to teach me how to use this device without virtual machine ill be grateful.

---

### Post by pytheas22 on 2011-12-18
Have you tried reading the aircrack documentation?  You could start by searching the [forums]("http://forum.aircrack-ng.org/index.php") for "rtl8191su"; a few seconds doing that led me to [this thread]("http://forum.aircrack-ng.org/index.php?topic=12242.0"), where someone says your device should work in Ubuntu with the latest kernel updates.

---

