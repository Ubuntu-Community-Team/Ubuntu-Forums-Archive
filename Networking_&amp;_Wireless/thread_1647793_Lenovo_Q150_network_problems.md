---
title: "Lenovo Q150 network problems"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by nmstewart on 2010-12-17
I am having the same problem as David Cash posted:

[http://ubuntuforums.org/showthread.php?t=1638660](http://ubuntuforums.org/showthread.php?t=1638660)

His issue was resolved with Lucid Lynx. However it did not resolve my problems.
All of the logs were nearly identical for the lspci and the 8086 grep.

I was wondering If Davids question could be reopened or can we continue it here.


My ultimate goal is to turn this box into an entertainment pc.


Thanks 

Neil

---

### Post by chili555 on 2010-12-17
Please run:```
lspci -nn
```Post the ethernet part and confirm that you are trying to get your wired ethernet going.

---

### Post by nmstewart on 2010-12-17
I realized that I forgot to mention that I was testing the Live CD and that I have not installed it yet


here is the lspci -nn

ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a000] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:08.0 Ethernet controller [0200]: Intel Corporation 82552 10/100 Network Connection [8086:10fe] (rev 02)
02:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce 310M] [10de:0a75] (rev a2)
02:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)

Thanks
Neil

---

### Post by chili555 on 2010-12-17
I appreciate the information. I still need the requested data. Thanks.

---

### Post by nmstewart on 2010-12-17
here it is again. I also did an install to see if there was a difference. Still the same

ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a000] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:08.0 Ethernet controller [0200]: Intel Corporation 82552 10/100 Network Connection [8086:10fe] (rev 02)
02:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce 310M] [10de:0a75] (rev a2)
02:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)

---

### Post by chili555 on 2010-12-17
Your ethernet device is supposed to work with the driver module *e100*. Let's load it and see if there are any kernel messages that tell us what's happening:```
sudo modprobe e100
dmesg | grep e100
```Thanks.

---

### Post by nmstewart on 2010-12-18
I loaded the e100 to no avail here is the dmesg:

elmo@:~$ dmesg | grep e100
[    1.021979] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.021985] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.022072] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.064090] e100 0000:01:08.0: PME# disabled
[    1.065421] e100: eth0: e100_probe: addr 0xfcfff000, irq 20, MAC addr 70:71:bc:6e:0c:3c


Thanks
Neil

---

### Post by chili555 on 2010-12-18
To no avail?? Sometimes there are clues in what is said as well as what is not said in the message logs. What is not said is 'error' or 'warning.' What is said is that an interface was created, eth0.

Please let us see:```
dmesg | grep eth0
ifconfig eth0
```Thanks.

---

### Post by nmstewart on 2010-12-18
here you go:

elmo@Ping-TV:~$ dmesg |grep eth0
[    1.487267] e100: eth0: e100_probe: addr 0xfcfff000, irq 20, MAC addr 70:71:bc:6e:0c:3c
elmo@Ping-TV:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 70:71:bc:6e:0c:3c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I also tried to research the PME# Disabled from the dmesg e100 but I havent found anything yet.

Thanks
Neil

---

### Post by nmstewart on 2010-12-18
Ok, 

 I feel horrible now. I had a power outage that shut down my PC. Now it works........


A cold re-boot after the modprobe would probably worked.



Humble Thanks 

Neil

---

### Post by chili555 on 2010-12-18
No worries; it happens to all of us. I'm just glad it's working.

---

### Post by jpage4500 on 2011-02-01
Hi,

I see that this was apparently solved by a power outage - but I'm having the same problems on my Q150. Network (LAN) works fine in Windows but not recognized in Linux (I've tried a few versions).

My question is - would any of the commands below actually do anything to resolve this? The seems to be more informational.. 

I'd hate to rely on rebooting this device until it works.. there's got to be some reason that LAN isn't working on it - but I just can't figure out what..

thanks
joe

---

### Post by chili555 on 2011-02-01
> would any of the commands below actually do anything to resolve this? Do you mean above? We won't know what will solve it until we have the information. Please post:```
lshw -C network
dmesg | grep eth
``` We'll go from there.

---

### Post by nmstewart on 2011-02-18
> **jpage4500 said:**
> Hi,

I see that this was apparently solved by a power outage - but I'm having the same problems on my Q150. Network (LAN) works fine in Windows but not recognized in Linux (I've tried a few versions).


I'd hate to rely on rebooting this device until it works.. there's got to be some reason that LAN isn't working on it - but I just can't figure out what..
thanks
joe

Joe,
I just repaved my Q150 with 10.10 meerkat. What I have found is the modprobe e100 works to load in the correct module. 
However when switching from windows to Ubuntu it would not work until power was removed completely. I had to disconnect the power supply when switching. I dont have this problem unless I actually boot into windows.

btw: I am still trying to tackle the wireless.

---

