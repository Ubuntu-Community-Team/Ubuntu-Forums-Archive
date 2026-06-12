---
title: "Ethernet Not Connecting"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by K_REY_C on 2009-12-05
When I got my Dell XPS1530 I had one hell of a time setting up/configuring the wireless [(link)]("http://ubuntuforums.org/showthread.php?t=1209055") but eventually it worked. I've now come to find out that the ethernet connection isn't working. 

The NetworkManager Applet will say that it has connected... but I am unable to connect to websites, etc... When I switch back to wireless (through the same router at home) all is fine.

It isn't the cable (as it works on other machines).

I fear I've screwed something up when making it work for wireless. I'd like to have both work. Can anyone help me with this problem? I've searched around and tried some different things (perhaps making it worse... but certainly confusing me more).

Here is some info that is typically asked for (Sorry that I don't understand the output!)

Thanks in advance!

> $ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)


>  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
vboxnet0  no wireless extensions.

pan0      no wireless extensions.

>  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
vboxnet0  no wireless extensions.

pan0      no wireless extensions.

>  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:00:27:41  
          inet6 addr: fe80::223:aeff:fe00:2741/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22712 (22.7 KB)  TX bytes:6133 (6.1 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:23:4e:c7:cd:0b  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4eff:fec7:cd0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18702 errors:0 dropped:0 overruns:0 frame:3781
          TX packets:16044 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12263511 (12.2 MB)  TX bytes:3023919 (3.0 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46105 (46.1 KB)  TX bytes:46105 (46.1 KB)


---

### Post by Iowan on 2009-12-05
eth1 is the wireless? What's in */etc/network/interfaces* (it should only have two lines defining "lo"). eth0 has no IP address - so I won't bother asking about gateway or nameservers... yet.

> **K_REY_C said:**
>  I'd like to have both work.Simultaneously? (It can probably be done)

---

### Post by Alexis Phoenix on 2009-12-05
Couple of things I notice - where you have quoted the output from iwconfig - the wireless link is not connected.

Where you have shown the output from ifconfig, apparently it is connected.  You say it's working so I'll assume this is just coincidental and there is no problem there.

If you look closely at the output of ifconfig for eth0, there is no ipv4 address - which you can see in the info for eth1.

I would try as root:```
dhclient eth0
```with the wire connected.  You should see messages saying it's requesting an ip number, then where it gets one, and the output finishes.

You may find (this happens to me) that you still can't connect to the internet.  In my case this is a routing problem - the simple fix is to close the interface I'm not using (as root):```
ifdown eth1
```.  I'm sure there's a better way but I haven't got round to finding out what it is yet.

HTH,
Alexis

---

### Post by K_REY_C on 2009-12-05
Here's what I've found out at this point:

I can connect to "Auto Ethernet" correctly and successfully as long as I disable Wireless (right click, uncheck "enable wireless")

I guess this is an acceptable solution for me... as I just wanted to be able to use ethernet if I need/want to... but it seems weird that it doesn't automatically switch to the faster/more stable connection.

Thanks for the quick responses. If you have any other thoughts please do let me know!

---

