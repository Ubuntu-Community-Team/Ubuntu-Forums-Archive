---
title: "Networking service suddenly won't start"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by dgray_from_dc on 2011-03-14
I've been using Kubuntu Lucid on a Compaq tc4200 for nearly a month now.  Suddenly today I logged into my machine and found that I couldn't connect to anything, Internet, LAN, router, nothing!  

Upon further investigation, I found that networking services weren't turned on at all!

I tried manually starting the network service using

```
sudo service networking start
sudo /etc/init.d/networking start
sudo /etc/init.d/networking force-reload

```

None worked.  The forced-reload triggers a 

```
* Reconfiguring network interfaces...                                                [OK]
```

But then, nothing happens.

I even tried (to no effect)

```
user@localhost:~$ iwconfig wlan0
wlan0     No such device
```

Sadly enough, I dual-boot this machine with XP Tablet PC Edition because I can't get the tablet functions working yet (long story for another thread).  But networking works fine there, so I know its not a hardware problem.  There have been no software updates that I can remember, and I haven't changed any settings, particularly those of the, before now, functioning network adapters.

Any help would be appreciated! :confused:

---

### Post by dgray_from_dc on 2011-03-15
Progress!!  (I think)

I tried ifconfig eth0 and got:

```
user@localhost:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:c0:9a:5d
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16
```

I assume that this means that my hard line works.  I'm going to give it a shot when I get back home and see whether or not I can at least use hard line networking.

---

### Post by SeijiSensei on 2011-03-15
Are you sure your wifi adapter is active?  Many notebooks have an Fn-key combination that turns the adapter on or off for power-saving purposes.  Perhaps you accidentally turned it off?  (A friend of mine did this not long ago and nearly tore her hair out wondering why she couldn't connect.)  Often you'll see a key with a little radio tower on it that represents the wifi switch.

---

### Post by viperce on 2011-03-15
try ifconfig -a

---

### Post by dgray_from_dc on 2011-03-15
I've cycled the Fn key for my WiFi radio several times.  No result.  Well, some result.  The WiFi indicator will pulse when WiFi is on but not connected, and remain steady off when the radio isn't on.  I get both of those conditions, but can't wake up the service in order to connect to anything.  As my original post states, I've had this machine functional for over a month now, until yesterday.

What concerns me here is the fact that before yesterday, whenever I logged in, the KDE Wallet asked me for a password so that the networking service could start.  It no longer does that.

I think wlan0 is mapped to eth1 so....

```
user@localhost:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:15:00:13:f0:e3
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x4000 Memory:d0400000-d0400fff
```

Since I only have 1 Ethernet port (RJ-45 connection) I assume this is my 802.11g.  This gives me some hope in that I'm pretty sure it hasn't lost any of the hardware and shouldn't require any special drivers.

Still, I can't figure out what's going on here... :confused: :confused:

---

### Post by dgray_from_dc on 2011-03-15
> **viperce said:**
> try ifconfig -a

I get the output in my previous posts for eth0, eth1, and loopback.

---

### Post by ant2ne on 2011-03-15
Can you plug in wired and get an IP address and browse the network? Plug in cable and do a ```
sudo dhclient eth0
``` If so, networking is up, and you should troubleshoot wireless device.

do a 
```
iwlist scanning
``` (maybe need sudo in front of that, i forget.) Do you see any wireless networks? If not, can you verify that your WAP up?

---

### Post by dgray_from_dc on 2011-03-15
> **ant2ne said:**
> Can you plug in wired and get an IP address and browse the network? Plug in cable and do a ```
sudo dhclient eth0
``` If so, networking is up, and you should troubleshoot wireless device.

do a 
```
iwlist scanning
``` (maybe need sudo in front of that, i forget.) Do you see any wireless networks? If not, can you verify that your WAP up?

Looks like my hard-line works!!

```
user@localhost:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:0f:b0:c0:9a:5d
Sending on   LPF/eth0/00:0f:b0:c0:9a:5d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPOFFER of 192.168.2.10 from 192.168.2.1
DHCPREQUEST of 192.168.2.10 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.10 from 192.168.2.1
bound to 192.168.2.10 -- renewal in 847256349 seconds.

```

```
user@localhost:~$ ping www.google.com
PING www.l.google.com (72.14.204.99) 56(84) bytes of data.
64 bytes from iad04s01-in-f99.1e100.net (72.14.204.99): icmp_seq=1 ttl=51 time=17.9 ms
64 bytes from iad04s01-in-f99.1e100.net (72.14.204.99): icmp_seq=2 ttl=51 time=20.2 ms

```

Unfortunately, the KDE network manager doesn't seem to know it.  It shows my network as unmanaged.  I can't look at settings, networks, or anything.

```
user@localhost:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

```

  This further reinforces my thought that there's nothing wrong with my hardware, just some sort of disconnect with the software.  On a command prompt level, I can see my adapters and connections (although I can't seem to connect via WiFi).

  Perhaps it's just the KDE network management system that's having problems.  Afterall, the GUI portion of WiFi has just always worked, I've never had to do it at the command prompt.

I am posting this from the machine in question, but via a network connection that KDE doesn't seem to see. :confused:

---

### Post by SeijiSensei on 2011-03-16
I'd try using System Settings > Network Settings to delete any existing wifi profiles and create a new one.  See if it can scan the network and find your access point.

---

### Post by dgray_from_dc on 2011-03-16
> **SeijiSensei said:**
> I'd try using System Settings > Network Settings to delete any existing wifi profiles and create a new one.  See if it can scan the network and find your access point.

As I explained before, the network manager doesn't work.  As far as I can tell, the KDE software will not recognize that there is even a vaild network adaptor on the system.

For the sake of being thorough, I tried it anyway.

Because I'm presently at work, from my 4G phone (to which I've successfully connected before) I turned on my WiFi Hotspot....

Then...

System Settings > Network Settings

I deleted all preexisting connections

Clicked **[Add...] **button

Stayed on the wireless tab

Clicked **[Scan] **button

It sees no WiFi networks.

Even at home yesterday, when I successfully connected via hard-line, the KDE network manager was unaware of it.  The notification icon in the task bar simply read unmanaged for my network status.

---

### Post by SeijiSensei on 2011-03-16
Do you know if you had a kernel upgrade recently?  When you boot, see how many kernels appear in the grub menu.  If there's an older kernel or two available, try selecting one of them and see if that helps.  It might be a regression in the wifi driver.

---

### Post by dgray_from_dc on 2011-03-16
> **SeijiSensei said:**
> Do you know if you had a kernel upgrade recently?  When you boot, see how many kernels appear in the grub menu.  If there's an older kernel or two available, try selecting one of them and see if that helps.  It might be a regression in the wifi driver.

I thought of that before.  I've had that type of issue before, but not with WiFi.  I currently have two kernels installed, neither works.

I'm thinking about trying to find which KDE module deals with networking and reinstalling it to see if something needs to be cleaned up.  However, I won't be able to do that until this evening when I get home.

By the way, thanks for the help so far....

---

### Post by dgray_from_dc on 2011-03-16
**_Found it!!!!_**

The answer was in a post on KDE.org entitled [[COLOR="Blue"]_*network manager disabled.*_[/COLOR]]("http://forum.kde.org/viewtopic.php?f=18&t=89863")

> Here is the easy fix, at least for me:
$ cd /var/lib/NetworkManager
edit the file "NetworkManager.state"
Change NetworkingEnabled=false to true
Save
reboot

This is from jkClarkson Sept 2007 in ubuntuforums.org
Thanks jc 




Followed the steps:

```
user@localhost:~$ sudo kate /var/lib/NetworkManager/NetworkManager.state
```

I changed false to true, saved, rebooted.

I've gotten my networking up, running, and connected to my 4G HotSpot.

Again, thanks to all for your help!!!

---

### Post by dgray_from_dc on 2011-05-12
Update:

This is a recurring problem that apparently comes about as a result of something going wrong during standby/suspends (particularly with laptops and netbooks upon closing the lid).

I've gotten it from **[here]("http://ubuntuforums.org/showthread.php?t=1475230")** and **[here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/553994")** that this is a KDE bug that was fixed as of KDE 4.5.4 (Lucid is still using 4.4.5).

---

