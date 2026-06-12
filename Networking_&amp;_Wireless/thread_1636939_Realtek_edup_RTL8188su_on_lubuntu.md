---
title: "Realtek edup RTL8188su on lubuntu?"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by Geerie on 2010-12-03
Hello guys,

I am pretty new to ubuntu, but sofar I am doing fine, searching alot about it right now, First I tried it a few times and finally it caught me :) So much in fact that I am promoting it while I have always told it was not my thing!

Anyways, been in ubuntu and I am trying to learn and pick up things fast and now ( I can't believe I am saying this :p ) I am promoting Lubuntu for usage on an old laptop of my girlfriends parents.

Telling them lubuntu wil be so much better then xp.
Xp runs very slow on it.
1 ghz 512MB of ram.
I tested the lubuntu cd on that old lappie and it seems to pick up most of the drivers pretty fast.

But I need help.
I read about how to install this edup rtl8188su somewhere in the forums. But I can not get it to work in ubuntu 10.10 x64 on my own lappie so my question is:
Does it work in lubuntu? Cause I don't wanna fail on them while I am promoting this overthere.

Can someone please explain on how to make it work? 
I am not good at installing drivers yet and I don't know if it is not a standard driver in lubuntu.
Must say I haven't tried the device yet while using the live cd.
Tommorow(today) I will install lubuntu and want to add this wireless device on it.

Plz help me out!
Thanks in advance

---

### Post by northd_tech on 2010-12-04
Hi Geerie,

To figure out exactly what kind of hardware you are running, will you open a terminal under Lubuntu (I believe that will be the same as "standard" Ubuntu:  Applications > Accessories > Terminal) and post the output from the following commands (copy & paste to prevent typos):

```
lspci 
sudo lshw -C Network
ifconfig
iwconfig

```Looking at this webpage, my "Applications >" above might actually be that blue Lubuntu icon at lower right of the screen, but the "Accessories" part still looks correct:

[http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Lubuntu%2010.04%20Alpha%203]("http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Lubuntu%2010.04%20Alpha%203")

---

### Post by Geerie on 2010-12-05
I did the following commands like you requested.

output 1:

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

output2:

Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.14)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)


output 3:

eth0      Link encap:Ethernet  HWaddr 00:0b:cd:87:3e:38  
          inet addr:192.168.1.27  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe87:3e38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39066459 (39.0 MB)  TX bytes:2061474 (2.0 MB)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1272 (1.2 KB)  TX bytes:1272 (1.2 KB)

output 4 without rtl8188su stick:

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Geerie on 2010-12-05
This is the output while the usb stick I mention was inside
The laptop is a hp e pavilion ze 4317ea


:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1


~$ sudo lshw -C networksudo lshw -C Network
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.14)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:87:3e:38  
          inet addr:192.168.1.27  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe87:3e38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39317316 (39.3 MB)  TX bytes:2146311 (2.1 MB)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1272 (1.2 KB)  TX bytes:1272 (1.2 KB)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by northd_tech on 2010-12-05
> **Geerie said:**
> **lspci**
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller

output2:
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.14)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

It looks like this is a USB wireless interface- can you post the output from 2 more terminal commands that I forgot to post earlier:

```
lsusb
lsmod

```I did find a Linux driver at the Realtek website for a RTL8188SU (and you want the "Unix (Linux)" version):

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true#2282](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true#2282)

It looks like there might be a typo in the **lshw** command above (unless lunbuntu uses a different format for some reason).  Let's try looking at that one again too (it is usually best to copy & paste the Linux command directly into the terminal window):

```
sudo lshw -C network
```

---

### Post by Geerie on 2010-12-05
Hello and thanks for helping.

It is indeed a usb wireless device. 
My bad that I forgot to mention that ](*,) 
I am unable to get to that laptop right now.
I will do these commands ASAP! 

I did copy paste them btw like you told me to.

Thanks.

---

### Post by Geerie on 2010-12-09
I retried that code herie it is:


duijn@ze4300:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:87:3e:38
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.27 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:11 ioport:8c00(size=256) memory:d0003000-d0003fff memory:24000000-2400ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:e0:4c:00:f3:e4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
duijn@ze4300:~$

---

### Post by Geerie on 2010-12-09
I also downloaded this driver set
rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625

I have no clue however on how to make it work or install it? :S

---

### Post by chili555 on 2010-12-09
I think my friend northd_tech will be interested in the firmware. Please insert the device and let him see:```
dmesg | grep -i firm
```Thanks.

---

### Post by Geerie on 2010-12-10
thanks I will do so at first opportunity tommorow morning :)

---

### Post by Geerie on 2010-12-11
duijn@ze4300:~$ dmesg | grep -i firm
[   27.634276] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   27.637664] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   27.817520] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   27.820555] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   28.015698] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   28.018168] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   28.199940] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   28.202966] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
duijn@ze4300:~$ sudo dmesg | grep -i firm
[sudo] password for duijn: 
[   27.634276] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   27.637664] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   27.817520] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   27.820555] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   28.015698] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   28.018168] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   28.199940] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   28.202966] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a

---

### Post by chili555 on 2010-12-11
This might help: [https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)

---

### Post by Spyderkid on 2010-12-11
okay do this...


1)run this in a terminal, (it extracts the driver):
```

tar zxvf rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.201006 25.tar.gz

```

2)go to the place where the driver was saved (probably the home folder)
  (so just type in this) 
```

make

```


3) run this... (this will run with root permissions don't worry)
```

sudo ./clean

```


4) insert 8712 USB modules, with root access (by running this)...
```

sudo insmod 8712u.ko

```

RESTART THE COMPUTER
then you should be done hope it worked

---

