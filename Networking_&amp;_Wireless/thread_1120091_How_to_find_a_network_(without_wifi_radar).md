---
title: "How to find a network (without wifi radar)"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by tp-owner on 2009-04-08
[Note:this is on ubuntu 8.10] Ok I have a zoom wireless dongle and I have installed a driver, From what I can see it works but I have included some test results anyway :D

I hope someone can point me in the right direction to getting my laptop connected to our NETWORK (set up via windows)

Entered:
```
sudo lshw -C network
```
Result:
```
 *-network DISABLED      
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:25:85:98:2a:40
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

Entered:
```
lspci -nn
```
Result:
```
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:02.0 CardBus bridge [0607]: Texas Instruments PCI1251A [104c:ac1d]
00:02.1 CardBus bridge [0607]: Texas Instruments PCI1251A [104c:ac1d]
00:06.0 Multimedia audio controller [0401]: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] [1013:6001] (rev 01)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 02)
01:00.0 VGA compatible controller [0300]: Neomagic Corporation NM2200 [MagicGraph 256AV] [10c8:0005] (rev 12)
06:00.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
06:00.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
06:00.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 02)


```

Enetered:
```
iwconfig
```
Result:
```

lo        no wireless extensions.

pan0      no wireless extensions.



```

Entered:
```
lsusb
```

Result:
```
bus 004 Device 002: ID 0803:4410 Zoom telephonics, Inc.
bus 004 Device 001: ID 1d6b:0002 Linux foundation 2.0 root hub
bus 004 Device 001: ID 1d6b:0001 Linux foundation 1.1 root hub
bus 004 Device 001: ID 1d6b:0001 Linux foundation 1.1 root hub
bus 004 Device 001: ID 1d6b:0001 Linux foundation 1.1 root hub
```

Entered:
```
sudo iconfig pan0
```

Result:
```
pan0 Link encap:Ethernet HWaddr 96:25:85:98:2a:40
inet6 addr: fe80::9425:85ff:fe98:2a40/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:468 (468.0 B)
```

---

### Post by rlzyoner on 2009-04-09
What is the result of

iwlist scan

This should return any wireless ap's that the card picks up.
The try connecting manually

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid THE_ESSID
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 key THE_WEP_KEY
dhclient3

This should manually conenct to the network using adaptor wlan0 (change accordingly) and then request a network address via dhcp

Is this what you were looking for ?

---

### Post by tp-owner on 2009-04-09
well the iwlist scan just tells me that lo and pan0 doesn't support scanning!

And the other bit does look like the right thing...

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid THE_ESSID - (I have never come accross ESSID)
sudo iwconfig wlan0 mode managed - (MODE?)
sudo iwconfig wlan0 key THE_WEP_KEY - (I know this LOL)
dhclient3 - (AGAIN... ?)

---

### Post by rlzyoner on 2009-04-09
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid THE_ESSID - (The 'name' of the wireless network)
sudo iwconfig wlan0 mode managed - (How the wireless card should function)
sudo iwconfig wlan0 key THE_WEP_KEY -
dhclient3 - (Request an ip address from the router)

Nevermind that though, it looks like your wireless card is not installed properly, what is the wireless card, is it inbuilt or usb.

Where is the driver for this card. 
If you are dualbooting then it is probably on the windows partition and you could use ndiswrapper to use the windows driver.

Post the output of 
lspci | grep Network

---

### Post by tp-owner on 2009-04-09
I am not dualbooting but I DID use a windows driver. Its usb and I have installed ndiswrapper, and the driver that i found on the zoom driver disc.

lspci | grep Network

this gave nothing.

---

