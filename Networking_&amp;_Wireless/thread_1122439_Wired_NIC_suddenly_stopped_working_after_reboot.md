---
title: "Wired NIC suddenly stopped working after reboot"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by BinaryMn on 2009-04-11
For the record, I've spent hours trying to figure out what has caused my problem and how to fix it and I'm still at square one. I'll start at the beginning trying to provide as many (important) details as possible. However, I'm going to give a slight background first.

I have two laptops. One running Ubuntu (Intrepid) with a small partition with XP Professional. Do note that this laptop has a busted CD/DVD-ROM and can only boot from USB (which is painfully slow). The other is running XP Professional.

Originally, I was trying to create a SMB share on Ubuntu pointing to my mounted external hard drive. I eventually gave up and ended up reversing the roles. I created a share for my external hard drive on the (second) laptop running XP Pro and was able to access it on Ubuntu.

So, I then used smbfs to make a mount point in /etc/fstab to mount the network share to /media/stuff. Ran "mount -a" and voila! Everything was working. As a side note, I have the laptops connected wired and set statically for transfer speeds.

About two hours later, I rebooted the laptop running Ubuntu. I log in and to my horror, my wired interface (eth0) has stopped working. It's like the NIC just suddenly stopped working. Both Ubuntu and XP Pro detect the NIC still, but it doesn't pick up a connection on the physical layer. I keep getting "ADDRCONF(NETDEV_UP): eth0: link is not ready" from dmesg if I bring eth0 down, then back up. I've run mii-tool and get back "no link". I've tried removing the driver and modprobing it with no luck. I've spent hours googling solutions and trying different methods. I thought I was getting somewhere when the networkmanager applet gave me "device is unmanaged" instead of listing "Auto eth0" and the static connection, but I fixed that by editing some config file in /etc/networkmanager and changing some line from false to true. I've even changed Cat5 cables to one I know that is working in case the one I was using went bad.

I've been using Linux for five years. I'd like to think I know enough to install and maintain a linux distro or a unix server. I'm a telecommunication/networking student in college and I'm completely stumped at what is happening here. Whenever I have a problem with Linux, I've been able to solve it just by googling the problem enough and I eventually find an answer, or I figure out how to fix it myself. At this point, I don't know what to do. I can't even get the LiveUSB image to boot (syslinux can't find the linux kernel image) right now and now I just keep getting a black screen after the blue loading bar if I try booting into Windows. I'm too exhausted to fight with this anymore right now so I'm hoping posting this will shed some advice when I wake up.

I'll post lspci below. Do note that the Ralink NIC is my wireless and the VIA VT#### NIC is the wired. Thanks in advance.

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
```

---

### Post by superprash2003 on 2009-04-11
does the NIC work on windows? post output of ifconfig and sudo /etc/init.d/networking restart from the terminal

---

### Post by BinaryMn on 2009-04-11
> **superprash2003 said:**
> does the NIC work on windows? post output of ifconfig and sudo /etc/init.d/networking restart from the terminal

> **BinaryMn said:**
> Both Ubuntu and XP Pro detect the NIC still, but it doesn't pick up a connection on the physical layer.

Or so it seems. It's almost like the NIC wasn't shut down properly, for lack of a better word, and is stuck in some mode that won't let it fully initialize up. Least, that's what it feels like.

```

eth0      Link encap:Ethernet  HWaddr 00:40:45:19:c0:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xae00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1048 (1.0 KB)  TX bytes:1048 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:09:09:0b:87  
          inet addr:192.168.2.26  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe09:b87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:48961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12214150 (12.2 MB)  TX bytes:4658470 (4.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-09-09-0B-87-62-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
chris@Ringo:~$ sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
```

I restarted the networking service once before and didn't get that error. It restarted fine the first time.

---

### Post by BinaryMn on 2009-04-11
Bump.

---

### Post by BinaryMn on 2009-04-12
> **BinaryMn said:**
> Bump.
](*,)

---

### Post by superprash2003 on 2009-04-13
well if it isnt working in both windows and ubuntu , i think your NIC is broken..

---

### Post by BinaryMn on 2009-09-23
The NIC was fine. It suddenly started working about two months ago all on its own.

---

