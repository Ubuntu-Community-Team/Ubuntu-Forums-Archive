---
title: "Belkin F5D7050"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by strongfan on 2009-04-15
Where can I download the Linux Drivers for my Belkin FD7050 card?  The wireless thing that came with my computer can only get a painful 1 megabyte per second, so I want to try using this one but I lost the CD long ago.  So where can I download the drivers?

---

### Post by RedSingularity on 2009-04-15
In terminal type lspci and post the output here on the forums.

---

### Post by strongfan on 2009-04-17
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
01:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 02)
```


there's the output

---

### Post by RedSingularity on 2009-04-17
What type of card is it?  Its not coming up on you PCI card list so i suspect its not PCI.

---

### Post by strongfan on 2009-04-18
It's not a card, persuea, it's a usb adapter.

---

### Post by RedSingularity on 2009-04-18
Oh ok, with the device plugged in do "lsusb" in terminal and post the output.

---

### Post by strongfan on 2009-04-18
```
Bus 005 Device 006: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 005 Device 005: ID 15a9:0004  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:c216 Logitech, Inc. Dual Action Gamepad
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0a5c:2101 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0461:4d16 Primax Electronics, Ltd 
Bus 001 Device 004: ID 03f0:7804 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

```

Here we are.  And how exactly will this help you find a driver?  That's all I need at the moment.

---

### Post by StuartN on 2009-04-18
> **strongfan said:**
> Here we are.  And how exactly will this help you find a driver?  That's all I need at the moment.

It should list something like "ID 050d:905b Belkin Components", but this hasn't appeared in your USB listing. This is a unique hardware code that identifies the manufacturer and product. Make sure the Belkin is listed and post the output again.

---

### Post by Crafty Kisses on 2009-04-18
Hey there strongfan! The only thing that remotely looks like a wireless/ethernet card in the lspci output is the following:
```
Bus 002 Device 003: ID 0a5c:2101 Broadcom Corp.
```
What are the results of these commands?
```
lsusb
lshw -C network
ifconfig
iwconfig
```
That will give me and other people more information on your setup. Once we get these outputs I or someone else can assist you further.

---

### Post by strongfan on 2009-04-19
> **Codename said:**
> Hey there strongfan! The only thing that remotely looks like a wireless/ethernet card in the lspci output is the following:
```
Bus 002 Device 003: ID 0a5c:2101 Broadcom Corp.
```
What are the results of these commands?
```
lsusb
lshw -C network
ifconfig
iwconfig
```
That will give me and other people more information on your setup. Once we get these outputs I or someone else can assist you further.

lsusb
```
Bus 005 Device 009: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 005 Device 006: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 005 Device 005: ID 15a9:0004  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0a5c:2101 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0461:4d16 Primax Electronics, Ltd 
Bus 001 Device 004: ID 03f0:7804 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
```

lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:1a:92:10:d3:45
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:73:03:40:16
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.108 multicast=yes wireless=IEEE 802.11g

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1a:92:10:d3:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89416 (87.3 KB)  TX bytes:89416 (87.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:03:40:16  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:62dc:b388:1234:21a:73ff:fe03:4016/64 Scope:Global
          inet6 addr: fe80::21a:73ff:fe03:4016/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:388356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:236058623 (225.1 MB)  TX bytes:26016096 (24.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-03-40-16-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Telstar"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:95:48:7A   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=63/100  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Crafty Kisses on 2009-04-19
Well it's recognized by lsusb, you have the following card:
```
Bus 005 Device 009: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
```
Try following these instructions: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver)](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver))

---

### Post by Philosofy on 2009-05-10
I seem to have the same problem, but its compounded by the fact that I don't know what the heck I'm doing (or supposed to be doing.)  I followed the link that has the instructions, but beyond that I'm at a loss.  I tried step one, and typed 
$ gksudo gedit /etc/modprobe.d/blacklist 
into the terminal, which opened up another window.  In that window I typed 

# The Edgy Eft zd1211rw module does not work in kernel 2.6.17
blacklist zd1211rw  

I have no idea if that worked.  I don't know if I have ndiswrapper or not.  The rest of the commands I typed into the terminal, but nothing seemed to happen.

Could someone be so kind to walk me through this like I am 5 years old?  I really need to get this computer up and running so I can bring my primary computer in for repairs.

Thanks

---

### Post by Philosofy on 2009-05-10
I found some of my mistakes: I don't need to type $ etc,

But now I'm stuck on steps 3 and 4. I type the wget command, and it looks like it downloads. But when I move on to the first step of Step 4, I get an error message:

phil@phil-laptop:~$ tar xvzf zd1211-driver-r83.tgz
tar: zd1211-driver-r83.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

