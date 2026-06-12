---
title: "RT2500 does not connect"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by Thidox on 2011-03-19
Hey,  I installed Ubuntu 10.10 on my old laptop the other day, but it seems that Wifi card is having some troubles with co-operating :(
  The wired connection works like a charm but I'd prefer wireless on the laptop....
I know the laptop is an oldy :P (PH Easynote R1904) 
 Perhaps you guys could tell me what's wrong?

 Thanks in advance, Thierry

Edit:

here's the LSPCI output:
```
00:00.0 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Network controller: RaLink RT2500 802.11g (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
```

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:40:d0:91:f1:09  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe91:f109/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8140972 (8.1 MB)  TX bytes:848866 (848.8 KB)
          Interrupt:11 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by Thidox on 2011-03-20
bump

---

### Post by MooPi on 2011-03-21
Can your adapter handle wep as well as wpa encryption ?

---

### Post by grahammechanical on 2011-03-21
You do not say what the troubles are. The listing from iwconfig tells me that you have a wireless adapter but it is not connected. ESSID: off/any. The message Tx power=0 dBm tells me that the wireless adapter is switched off. Tx power = transmitting power strength.

Why is it switched off. It there a switch on the keyboard that has not been activated? Do you have a driver for the wireless adapter installed? Go to system>Administration>Additional Drivers and activate any drivers that are offered to you. You need internet access for this to work.

May be you have done all of this but as you do not say what you have done or what messages you are getting as you try to use wireless to connect to the modem/router, then we have to start from the beginning.

Regards.

---

### Post by Thidox on 2011-03-21
the wireless connection is indeed switched off,
but enabling it throws me an error... :(

here it is:

with cable plugged in:
```

SCIOCSIFFLAGS: Devices or resource busy

```without cable plugged in:
```

enable: Unknown host
ifconfig: '--help' gives usage information

```
For as far as I know my laptop does not have a key to turn wi-fi on or off, so that's out of the question.

I also tried hard setting the configuration, but then still it doesn't want to work...

The additional driver list stays completely empty. (is this normal?)

edit:

after running dmesg I saw the following errors:
```

[   14.463304] rt2500pci 0000:00:06.0: enabling device (0000 -> 0002)
[   14.463317] rt2500pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq


--------


[   77.132976] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).

```

Might that be the issue?
if so, how do I fix it?

---

### Post by Thidox on 2011-03-26
bumptiebump....

---

