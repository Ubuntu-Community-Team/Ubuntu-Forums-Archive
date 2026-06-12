---
title: "Linksys Gigabit NIC Problem"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by andrewbrown22 on 2009-04-09
I seem to be having issues with a driver or something else related to my gigabit network card. It is a Linksys EG1032v3 (at least I assume it's version 3, that is the WinXP driver I used).
I have this card set up in a dual booting machine that dual boots Ubuntu 8.04 and Windows XP. I think it's been happening since the install, but I've only noticed it lately that the transfer speeds in Ubuntu are quite a bit slower than those on the same machine in Windows XP.
I did nothing to make the card work in Ubuntu, it worked right after the installation, ie I didn't install any "drivers" on the Linux partition.

Today I set up a test to see how different the transfer speeds were.  Here's what I found:
I transferred the Ubuntu 8.10 LiveCD (698.8 MB) to each partition from within the respective OS.    [note: the transfer was from my server via samba. This server is connected to a D-Link gigabit switch via Cat6 cable, just like the desktop in question.]

When transferring the file to Ubuntu, it took 18 minutes and 4 seconds.
When transferring to Win XP, it took 24 seconds.

I've also been noticing that VNC on that particular desktop is overly sluggish.

What could be the cause of this? What can I do to fix it?

---

### Post by pytheas22 on 2009-04-10
First of all, keep in mind that the slow transfer speeds over samba might reflect a problem with just samba, not with your ethernet connection in general.  I would do a test using another protocol as well to confirm that it's definitely the connection itself (don't trust VNC 'feeling' sluggish; there are a host of potential reasons for VNC to be slow that are unrelated to the ethernet.  I'd try downloading something over http or ssh to get a concrete comparison between Windows and Ubuntu.)

If you're sure the ethernet card is not working at full speed, post the output of these commands and I'll try to help:
```

lshw -C Network
ifconfig
lspci -nn
dmesg | grep eth
```

---

### Post by andrewbrown22 on 2009-04-10
I know it shouldn't be an issue with the samba configuration on the server because I transferred the same exact file from the server to the exact same computer on a dual boot configuration. 
That would leave the only difference being the way Ubuntu sees the NIC.

Here's the output I found:
```

andrew@desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Gigabit Network Adapter
       vendor: Linksys
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: eth0
       version: 10
       serial: 00:18:f8:0c:d0:e6
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.3 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
andrew@desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f8:0c:d0:e6  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f8ff:fe0c:d0e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4370305 (4.1 MB)  TX bytes:791040 (772.5 KB)
          Interrupt:20 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:124900 (121.9 KB)  TX bytes:124900 (121.9 KB)

andrew@desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 0e)
00:01.0 PCI bridge [0604]: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port [8086:2581] (rev 0e)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 [8086:2664] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
01:03.0 Mass storage controller [0180]: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 [1283:8211] (rev 11)
01:0a.0 Ethernet controller [0200]: Linksys Gigabit Network Adapter [1737:1032] (rev 10)
06:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7600 GT] [10de:0391] (rev a1)
andrew@desktop:~$ dmesg | grep eth
[   33.763546] eth0: RTL8110s at 0xf8842c00, 00:18:f8:0c:d0:e6, XID 04000000 IRQ 20
[   35.724186] Driver 'sd' needs updating - please use bus_type methods
[   35.724521]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   49.139991] r8169: eth0: link up
[   60.191306] eth0: no IPv6 routers present

```

---

### Post by pytheas22 on 2009-04-10
> I know it shouldn't be an issue with the samba configuration on the server because I transferred the same exact file from the server to the exact same computer on a dual boot configuration.
That would leave the only difference being the way Ubuntu sees the NIC.

There could still be a problem with the samba configuration on the client's (i.e., Ubuntu's) end.  I think it would still be worthwhile to see if you experience the same performance problems using a different protocol for transferring the data.

I googled and unfortunately couldn't find other people having performance issues with your hardware on Ubuntu.  The only other place I can think to look is to take a packet dump using Wireshark and see if anything strange comes up.  But please try testing with a protocol other than samba first, and we can go from there.

---

### Post by andrewbrown22 on 2009-04-10
Ok, I'll try to give http a shot at it and see how that turns out.

---

### Post by andrewbrown22 on 2009-04-10
I think you're on to something. Transferring it over http I got a much better speed (though still not up to the same speed as Samba on WinXP) than I had before. 
Ubuntu's file transfer window said it was right around 4MB/sec.  What could be wrong with my client's samba config?

---

### Post by cariboo on 2009-04-10
You can use iperf to check transfer speeds. Iperf is in the repositories. Install iperf on your server and on your desktop. Start iperf in server mode on the server with the following command:

```
iperf -s
```

then on your desktop open a terminal and type:

```
iperf -c <servername or ip address>
```

THe result I get on the desktop:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.100 port 47404 connected with 192.168.1.200 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec    115 MBytes  95.5 Mbits/sec
```

and the result on the server:

```
iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.200 port 5001 connected with 192.168.1.100 port 47404
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.2 sec    115 MBytes  93.9 Mbits/sec
```

There is also a windows version of iperf, that must be run on the command line.

Jim

---

### Post by pytheas22 on 2009-04-11
If you google something like 'ubuntu samba slow', there are lots of links to people reporting problems that sound like yours.  In particular, you might want to take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=424063&page=1") and this [bug report]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/84782").  There are various potential solutions suggested, including changes to samba configuration files and recompiling the ethernet driver.

A lot of people report having problems with only certain kinds of ethernet cards (those using the r8169 driver, like yours), so you could also think about buying a cheap PCI ethernet device with a different kind of chipset (something from Intel, for example).

As a third option, you could also consider changing your file server to use a protocol other than samba.  NFS, for example, works with both Windows and Linux, and since it's native to Linux (and open-source), Ubuntu would likely agree with it better than it does with samba (which is native to Windows, proprietary and closed-source).

---

### Post by andrewbrown22 on 2009-04-13
Is there a driver to download for this card for linux? I guess I don't really know how to install a driver in linux because everything has just worked for me so far.

If not, I guess I could get an Intel based gigabit PCI card, but I'd rather spend that ~$25 on something else if I could figure out this driver business.

---

### Post by pytheas22 on 2009-04-13
The Linux driver for your card is already included in Ubuntu.  I couldn't find any other drivers purported to work better.  It's possible that you could use ndiswrapper to drive the device, but please go through the bug report and thread I linked to and try the other possible fixes first.

---

