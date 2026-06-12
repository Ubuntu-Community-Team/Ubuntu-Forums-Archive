---
title: "Cannot Connect Ethernet, But Can Connect Wireless"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by kaufmed on 2009-08-29
Ubuntu Version: Intrepid Ibex

I used to be able to connect via ethernet to my router, but currently I cannot. Wireless connects fine, and I am able to browse internet, but as far as ethernet, I cannot connect. I am trying to transfer a large number of files from one computer to another, so using the ethernet is more preferable.

I am not sure which settings I should post, so please let me know :)

---

### Post by argos3016 on 2009-08-29
Try checking the settings in networkmanager, at notification area.

---

### Post by dbalascak on 2009-08-29
Did you stop/shutdown the wireless link when you make the wired connection?
Do you have a firewall running e.g. Firestarter.  You will need to set the interface in it if you switch.

---

### Post by g2k556 on 2009-08-29
I'm having a similar problem on my new Asus Aspire Timeline. When I go into network tools and devices, eth0 doesn't show. Any help is much appreciated. Thanks in advance, Gavin.

Here is lspci hopefully it's helpful
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

---

### Post by kaufmed on 2009-08-29
Here is what I have for settings in Network Configuration:

Now I do have two ethernet connections showing (which I find weird). I have tried removing one and working with the other, but the one I remove comes back.

For auto eth0:
    Connect Automatically - Checked
    System Setting - Unchecked
    Wired
        Mac Address: <Blank>
        MTU: Automatic
    802.1x Security
        Use 802.1x Security for this Connection: Unchecked
    IPV4 Settings
        Method: Automatic (DHCP)
        DHCP Client ID: <Blank>
    Routes - Nothing listed

There is no proxy enabled either.

---

### Post by kaufmed on 2009-08-29
Sorry, forgot Auto eth0 (second connection)

Auto eth0

Connect Automatically - Checked
    System Setting - Checked
**     Wired**
        Mac Address: set
        MTU: Automatic
**     802.1x Security**
        Use 802.1x Security for this Connection: Unchecked
**     IPV4 Settings**
        Method: Automatic (DHCP)
        DHCP Client ID: <Blank>
    Routes - Nothing listed

---

### Post by dbalascak on 2009-08-29
Can you post these 
**ifconfig -a** wired and wireless
**more /etc/network/interfaces** only once
**more /etc/NetworkManager/nm-system-settings.conf** only once
**ls /etc/NetworkManager/system-connections** wired and wireless

---

### Post by kaufmed on 2009-08-29
> **dbalascak said:**
> Can you post these 
**ifconfig -a** wired and wireless
**more /etc/network/interfaces** only once
**more /etc/NetworkManager/nm-system-settings.conf** only once
**ls /etc/NetworkManager/system-connections** wired and wireless

**ifconfig -a**
```
eth0      Link encap:Ethernet  HWaddr 00:18:8b:b9:1f:93  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:7067 errors:39 dropped:1 overruns:0 frame:35
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2115733 (2.1 MB)  TX bytes:1845 (1.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13760 (13.7 KB)  TX bytes:13760 (13.7 KB)

pan0      Link encap:Ethernet  HWaddr c6:6c:6f:bb:cc:95  
          inet6 addr: fe80::c46c:6fff:febb:cc95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:95047 (95.0 KB)

pan0:avahi Link encap:Ethernet  HWaddr c6:6c:6f:bb:cc:95  
          inet addr:169.254.9.149  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:09:3b:1d  
          inet addr:192.69.69.57  Bcast:192.69.69.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe09:3b1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74609783 (74.6 MB)  TX bytes:6476039 (6.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-09-3B-1D-62-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```**more /etc/network/interfaces**
```

auto lo
iface lo inet loopback

```[B]more /etc/NetworkManager/nm-system-settings.conf
[/B]```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```**ls /etc/NetworkManager/system-connections**
```

<nothing returned>

```

---

### Post by g2k556 on 2009-08-29
here are my results, each is labeled in the quote by

[quote=ifconfig -a]

**Only wireless showed, how do i do it for wired?**

**lo **       Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2480 (2.4 KB)  TX bytes:2480 (2.4 KB)

**pan0**      Link encap:Ethernet  HWaddr 0e:0d:34:3b:13:83  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**wlan0**     Link encap:Ethernet  HWaddr 00:17:c4:87:3e:1d  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:c4ff:fe87:3e1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20096 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28305620 (28.3 MB)  TX bytes:4023156 (4.0 MB)

**wmaster0**  Link encap:UNSPEC  HWaddr 00-17-C4-87-3E-1D-65-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[/quote]

[quote=more /etc/network/interfaces]
auto lo
iface lo inet loopback
[/quote]

[quote=more /etc/NetworkManager/nm-system-settings.conf]
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
[/quote]

[quote=ls /etc/NetworkManager/system-connections] Doesn't do anything :( [/quote]

---

### Post by dbalascak on 2009-08-29
ok. So both of you are NOT using NetworkManager to configure the interfaces as the file */etc/NetworkManager/nm-settings.conf* shows Managed=false. NetworkManager will not look for any interfaces.

Kaufmed
Your interface eth0 has an MTU size of 64. This is not correct. Should 1500.  This the maximum size of ethernet packet that the interface will send. See if you can set it with 
```
sudo ifconfig eth0 mtu 1500
```

If this seems to be acceptted do an *ifconfig -a* to confirm it. Plug in the ethernet cable and do teh same *ifconfig -a* command. You should see an IP address assigned to the interface eth0.  If this is true, you will need to set up NetworkManager so that you can switch between the two interfaces.


g2k556
Your network card is not being seen by the system.  Kaufmed, did you load drivers or anything to have your system recognize you LAN cand?

---

### Post by bkratz on 2009-08-29
> **dbalascak said:**
> ok. So both of you are NOT using NetworkManager to configure the interfaces as the file */etc/NetworkManager/nm-settings.conf* shows Managed=false. NetworkManager will not look for any interfaces.



g2k556
Your network card is not being seen by the system.  Kaufmed, did you load drivers or anything to have your system recognize you LAN cand?



g2k556      Recently a gentleman had a similary problem and discovered that the network card was not turned on in the bios---everything worked after changing this.

Good Luck

---

### Post by g2k556 on 2009-08-29
pretty much what I figured. It never asked me to install restricted network drivers and when I go to "Hardware Drivers" it doesn't recognize any restricted drivers in use. So how would I go about getting the computer to recognize it? My wireless works okay, it's kind of in and out with the internet, which is a pain, which is why I really want to use wired. I don't know yet if its my laptop that's causing the bad wireless connection or if it's our actual network. My brother seems to be connected fine on is windows machine, so I'm thinking it could be something wrong with my laptop, but I will be able to confirm this once I get it onto another network to see.

---

### Post by kaufmed on 2009-08-29
I believe I am using Network Manager (forgive me, I work mostly in Windows). As I said before, I can connect to wireless networks and switch between wireless networks, using what I believe to be Network Manager (the icon in my top panel which looks like signal-strength bars). When I use this applet to switch to eth0, however, it says that it is trying to acquire an address for eth0, but it fails and switches back to an available wireless network.

---

