---
title: "Can't Connet to internet"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by Turtlicious on 2011-05-29
I can't connect to my wireless router with my EEEpc 1001px,

If I turn on WEP key encryption it tells me I have a bad password, if I try to connect to an unencrypted network it just won't find the IP and just hang there.

I tried Network Manager and the switched to wicd to try and fix the problem.

Weird thing is, it just started this morning. I haven't installed anything new, downloaded anything new. Just out of nowhere the internet broke.

I really hope you can help me. Thank you so much in advance.

---

### Post by poolet on 2011-05-29
hello, paste the following output:: 

```

sudo lshw -C network

``````

iwconfig

``````

lspci or lsusb if your wireless card is a usb 
```**Note:** do you try to change the secure mode in your modem??

---

### Post by Turtlicious on 2011-05-29
sudo lshw -c network
```
PCI (sysfys)
```
iwconfig
```
  description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:7d:b1:25
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: bc:ae:c5:23:87:f9
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.197 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
justin@Ipod:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HDN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by josephmills on 2011-05-29
have you tried to soft reset you router? if that wont do the trick try hardline reseting it.

---

### Post by Turtlicious on 2011-05-29
XD

Did that while waiting for a reply, still no progress.

---

### Post by poolet on 2011-05-29
You need to download and install the drivers manually 

[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

---

### Post by josephmills on 2011-05-29
```
lsmod | grep ath 
``` and a ```
dmesg | grep ath 
``` thanks

---

### Post by Turtlicious on 2011-05-29
```
justin@Ipod:~$ lsmod | grep ath
ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath

```

```
justin@Ipod:~$ dmesg | grep ath
[    0.942450] device-mapper: multipath: version 1.2.0 loaded
[    0.942458] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.905863] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.905887] ath9k 0000:02:00.0: setting latency timer to 64
[   13.957410] ath: EEPROM regdomain: 0x60
[   13.957418] ath: EEPROM indicates we should expect a direct regpair map
[   13.957427] ath: Country alpha2 being used: 00
[   13.957433] ath: Regpair used: 0x60
[   14.050650] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.057935] Registered led device: ath9k-phy0::radio
[   14.058229] Registered led device: ath9k-phy0::assoc
[   14.058516] Registered led device: ath9k-phy0::tx
[   14.058789] Registered led device: ath9k-phy0::rx

```

---

### Post by Turtlicious on 2011-05-29
> **poolet said:**
> You need to download and install the drivers manually 

[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

Those links are for 10.10 & 10.4

I have 11.04

---

### Post by josephmills on 2011-05-29
```
rfkill list all 
``` and ```
lspci -nn
``` thanks

---

### Post by Turtlicious on 2011-05-29
```
justin@Ipod:~$ rfkill list all
0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
```
justin@Ipod:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

```

---

### Post by josephmills on 2011-05-29
more info ```
uname -a 
``` thanks looks like it is a kernel bug. like dude wheres my firmware.:P

---

### Post by Turtlicious on 2011-05-29
```
justin@Ipod:~$ uname -a
Linux Ipod 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

```

Thank you so much for helping me, I really appreciate it.

---

### Post by josephmills on 2011-05-29
please open up ubuntu software center then go to Edit-->software sources then make sure that all are ticked see pic Now close out of software sources and ubunut software center. Then do a ```
sudo apt-get update && sudo apt-get upgrade
``` reboot any wireless ? if not could we see a ```
lsmod | grep ath && dmesg | grep ath 
```thanks

---

### Post by Turtlicious on 2011-05-29
```
justin@Ipod:~$ lsmod | grep ath && dmesg | grep ath
ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
[    0.942450] device-mapper: multipath: version 1.2.0 loaded
[    0.942458] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.905863] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.905887] ath9k 0000:02:00.0: setting latency timer to 64
[   13.957410] ath: EEPROM regdomain: 0x60
[   13.957418] ath: EEPROM indicates we should expect a direct regpair map
[   13.957427] ath: Country alpha2 being used: 00
[   13.957433] ath: Regpair used: 0x60
[   14.050650] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.057935] Registered led device: ath9k-phy0::radio
[   14.058229] Registered led device: ath9k-phy0::assoc
[   14.058516] Registered led device: ath9k-phy0::tx
[   14.058789] Registered led device: ath9k-phy0::rx

```

---

### Post by josephmills on 2011-05-29
```
sudo apt-get remove linux-firmware && sudo apt-get install linux-firmware 

``` anything?

---

### Post by Turtlicious on 2011-05-29
no, should I just back up my important files and re-install ubuntu?

It worked until this morning

---

### Post by josephmills on 2011-05-29
that is up to you I can not seem to find the trouble maybe it is the driver/firmware but I can not find anything wrong with it(sorry) maybe someone else will. Have you tried it with just network manager no wicd and also you swear to me that you have hard line reset the router (button on the bottom of the router sometimes ) you have held that down until it has reset?

---

### Post by Turtlicious on 2011-05-29
XD I pinkie swear.

I'm not against it really, I just hate doing it.

I mess something in Ubuntu almost weekly now.

---

### Post by josephmills on 2011-05-29
try 10.10 I love it. But if you really like unity stick with 11.04 but there is more troubles to come if you do. I think that the kernel that 11.04 is using is not in my invitational list. It will get better but for right now there are bugs like this one. and so many others that I have seen. what would be cool is if I had a magic stick that said hey linus this kernel needs these patches. And somehow he would just sign off on them but until that day we will get all these bugs. I mean If I had that much raw power I would think that patches would come everyday. But they are not bummer. at any rate I hope you get this fixed up sorry that I could not help. have a good one.

---

### Post by Turtlicious on 2011-06-16
Solved: Resetted the router and found an option that says "Wake up" on the router web page.

Pressed that and I was able to connect.

^~^ Thank you JosephMills for the help

---

