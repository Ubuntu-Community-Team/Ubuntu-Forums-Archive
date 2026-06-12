---
title: "d-link dwa 525, not working on ubuntu 10.04"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by Vpc on 2011-09-08
I recently upgraded from 8.04 to 10.04.03 via the alternate installtion iso (no network connection at home). I am trying to connect to the wireless signal available. I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=1801363&page=2](http://ubuntuforums.org/showthread.php?t=1801363&page=2)

But
System -> Preferences -> Network Connections -> Wireless, lists no connections

administrator@snoopy:~$ sudo lshw -C network
[sudo] password for administrator: 
  *-network:0             
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 34:08:04:2d:7b:29
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:21 memory:ff8f0000-ff8fffff
  *-network:1 DISABLED
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 01
       serial: 00:11:11:3f:31:1c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:ff8ef000-ff8effff ioport:bc00(size=64)
===

administrator@snoopy:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Network controller: RaLink Device 3060
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)

administrator@snoopy:~$ lsmod
rt3562sta             916246  1 

127.0.1.1 snoopy

---

### Post by fdrake on 2011-09-08
> 
*-network:1 DISABLED
description: Ethernet interface

how are you online if the wired connection is down? is the wired connection working now?


can you please post here the content of /etc/modprobe.d/blacklist?
copy and paste please
```

gedit /etc/modprobe.d/blacklist
rfkill list all #copy and paste the output of this command.

```




edit: after looking at the installation link

---

### Post by Vpc on 2011-09-09
> **fdrake said:**
> how are you online if the wired connection is down? is the wired connection working now?


Obviously I'm not using my home computer to post to this forum.

> **fdrake said:**
> 
your wireless driver is not enabled.
can you please post here the content of /etc/modprobe.d/blacklist?
copy and paste please
```

gedit /etc/modprobe.d/blacklist
rfkill list all #copy and paste the output of this command.

```


I only added "blacklist rt2800pci" at the end of /etc/modprobe.d/blacklist following the instructions in the link in at the top of my initial post, nothing else is changed. What should I look for when I execute the rfkill? And how would I enable the wireless driver?

---

### Post by fdrake on 2011-09-09
what's the output for:

```

nm-tool
iwconfig
sudo iwlist scan
```

also with "rfkill list all" command did you see if any thing was blocked?

---

### Post by ratcheer on 2011-09-09
Let's get started. Please post the output of "sudo lspci -v", just the section for your wireless card.

I will have to be in and out, as I homeschool my son.

Tim

---

### Post by josh6190 on 2011-09-09
So the connection worked in 8 and not in 10? Whats the chance the drivers for that card were dropped in the update? Perhaps the install didnt go correctly and it didnt properly initialize the network card? Just throwing some trouble-shooting ideas out there.

---

### Post by Vpc on 2011-09-09
> **fdrake said:**
> what's the output for:

```

nm-tool
iwconfig
sudo iwlist scan
```

also with "rfkill list all" command did you see if any thing was blocked?

No output from "rfkill list all". Accidentally ran nm_tool instead of nm-tool so have to try that one again. Below is the output from the other commands:

```

administrator@snoopy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

==
administrator@snoopy:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:11:24:8D:09:1D
                    Protocol:802.11b/g
                    ESSID:"internet"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:37/100  Signal level:-75 dBm  Noise level:-81 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 70:71:BC:48:BE:22
                    Protocol:802.11b/g
                    ESSID:"Tulipan"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:42/100  Signal level:-73 dBm  Noise level:-68 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1F:F3:C1:D1:3A
                    Protocol:802.11b/g/n
                    ESSID:"Lucy's Network"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:31/100  Signal level:-77 dBm  Noise level:-72 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```

Also, I was given the password to connect to the network under "Cell 03" with ESSID:"Lucy's Network".

---

### Post by Vpc on 2011-09-09
> **ratcheer said:**
> Let's get started. Please post the output of "sudo lspci -v", just the section for your wireless card.

I will have to be in and out, as I homeschool my son.

Tim

Thanks. The output for the wireless card section:

administrator@snoopy:~$ sudo lspci -v

01:00.0 Network controller: RaLink Device 3060
	Subsystem: D-Link System Inc Device 3c04
	Flags: bus master, slow devsel, latency 32, IRQ 21
	Memory at ff8f0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Kernel driver in use: rt2860
	Kernel modules: rt3562sta

---

### Post by Vpc on 2011-09-09
> **josh6190 said:**
> So the connection worked in 8 and not in 10? Whats the chance the drivers for that card were dropped in the update? Perhaps the install didnt go correctly and it didnt properly initialize the network card? Just throwing some trouble-shooting ideas out there.

Actually in 8 I was using a direct wired connection to a modem. I currently don't have my own internet service at home (I am using a public computer right now) and am trying to connect to the wireless network available in my building.

---

### Post by ratcheer on 2011-09-09
Ok. Your driver and kernel module look good.

You already said you have rt2800pci blacklisted. It looks like you have rt3562sta in your /etc/initramfs-tools/modules. If so, that is all good. I really don't see what could be wrong. Do other wireless devices connect successfully to your wireless access point?

All I do to get wireless working from that point is:

sudo modprobe rt3562sta

and my connection comes right up. Also, I only have to do this once, it connects automatically after each reboot. Of course, every time the Linux kernel is upgraded, I have to go through the whole process, again (make, make install, and modprobe). But it only takes a couple of minutes.

I hope this is of some help. If not, I'm not sure what else to tell you.

Tim

---

### Post by ratcheer on 2011-09-09
Two other things. Is there a file rt2860.bin in /lib/firmware? Also, is RTA2860STA.DAT in /etc/Wireless/RT2860STA?

Tim

---

### Post by fdrake on 2011-09-09
can you please tell us what's the name of the network you r trying to connect to? also can you post the output of nm-tool.

@ratcheer
the fact that everything looks ok is kinda strange even for me. Maybe it's just a problem with the wireless manager?(infct with iwlist he can scan the networks). Also to note that **[COLOR="Red"]rfkill did not output anything[/COLOR]**(that means something is not fully recognized). Maybe he/she should just try to reinstall again the driver. step by step.

---

### Post by Vpc on 2011-09-10
> **ratcheer said:**
> Ok. Your driver and kernel module look good.

You already said you have rt2800pci blacklisted. It looks like you have rt3562sta in your /etc/initramfs-tools/modules. If so, that is all good. I really don't see what could be wrong. Do other wireless devices connect successfully to your wireless access point?

All I do to get wireless working from that point is:

sudo modprobe rt3562sta

and my connection comes right up. Also, I only have to do this once, it connects automatically after each reboot. Of course, every time the Linux kernel is upgraded, I have to go through the whole process, again (make, make install, and modprobe). But it only takes a couple of minutes.

I hope this is of some help. If not, I'm not sure what else to tell you.

Tim

Thanks. There are other 3-4 other computers connecting to the router (Apple Airport) for their internet access although I am probably the first person to try to connect with a Linux machine. I was told the previous occupant of my apartment was also able to connect. 

> **ratcheer said:**
> Two other things. Is there a file rt2860.bin in /lib/firmware? Also, is RTA2860STA.DAT in /etc/Wireless/RT2860STA?

Tim

Yes I have those files in those directories, except the ".DAT" is in lowercase.

---

### Post by Vpc on 2011-09-10
> **fdrake said:**
> can you please tell us what's the name of the network you r trying to connect to? also can you post the output of nm-tool.



I'm trying to connect to "Lucy Anima's Network" (the last WAP listed below or "Lucy's Network" in my post #7), see output of nm-tool below:

```

administrator@snoopy:~$ nm-tool

NetworkManager Tool

State: connected

- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        34:08:04:2D:7B:29

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BELL490:         Infra, 00:22:A4:50:EB:81, Freq 2462 MHz, Rate 0 Mb/s, Strength 100 WEP
    My network:      Infra, 00:24:01:29:C5:17, Freq 2437 MHz, Rate 54 Mb/s, Strength 2 WPA WPA2
    foxxyg:          Infra, 00:11:24:5F:FD:B7, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Tulipan:         Infra, 70:71:BC:48:BE:22, Freq 2437 MHz, Rate 54 Mb/s, Strength 2 WPA WPA2
    Fizz:            Infra, 00:22:2D:7A:60:74, Freq 2462 MHz, Rate 54 Mb/s, Strength 13 WPA2
    internet:        Infra, 00:11:24:8D:09:1D, Freq 2412 MHz, Rate 54 Mb/s, Strength 23 WPA WPA2
    Lucy Anima's Network: Infra, 00:1F:F3:C1:D1:3A, Freq 2442 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unmanaged
  Default:           no
  HW Address:        00:11:11:3F:31:1C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

```

> **fdrake said:**
> 
@ratcheer
the fact that everything looks ok is kinda strange even for me. Maybe it's just a problem with the wireless manager?(infct with iwlist he can scan the networks). Also to note that **[COLOR="Red"]rfkill did not output anything[/COLOR]**(that means something is not fully recognized). Maybe he/she should just try to reinstall again the driver. step by step.

I've think I've already tried to reinstall the driver, possibly a few times. Maybe it is "a problem with the wireless manager" as you say so I've downloaded NetworkManager-0.9.0 and nm-applet. [http://projects.gnome.org/NetworkManager/?x=22](http://projects.gnome.org/NetworkManager/?x=22)
I currently don't see the network manager in the taskbar like I used to so maybe that's another sign of a problem. I don't know what version of NetworkManager I currently have.

---

### Post by ratcheer on 2011-09-10
I have come across reports (I couldn't say where, now) that some people have to disable or uninstall either wicd or network manager, depending on which one they want to use. I have not had to do that, though.

Tim

---

### Post by praseodym on 2011-09-10
> **ratcheer said:**
> I have come across reports (I couldn't say where, now) that some people have to disable or uninstall either wicd or network manager, depending on which one they want to use. I have not had to do that, though.

Tim

Please show:

```
ps aux | grep Network
```
Try:

```
sudo service network-manager stop
sudo service wicd restart
```
The interface name changed from wlan0 to ra0, check your wicd-settings. Networkmanager has to be deactivated in Autostart

[COLOR="Red"]Edit[/COLOR]: In Lucid the network-manager better is uninstalled, you may also install the Wicd-add-on for different encryption modes:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get remove --purge network-manager network-manager-gnome
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service wicd restart
```
Be sure to use "wext" as driver in wicd.

---

### Post by Vpc on 2011-09-18
My wired internet was activated and I was able to get the Network Manager to appear in the taskbar and connect to the wired internet by changing managed=false to true in /etc/NetworkManager/nm-system-settings.conf and then rebooting. I don't have wicd installed and don't think it's needed since NM is now working ok.

However, I am still unable to connect to the wireless network that is available. I can see the password for the network in the Network Manager but NM keeps on trying to connect without any success (the NM icon keeps showing the animation indicating that it's trying to connect). I think this is related to the fact that I when I try to access [http://192.168.1.254/](http://192.168.1.254/) to check out the configuration for my wired internet (as instructed by my wired ISP) it continues to prompt me for my password after I enter it. I confirmed with my ISP that I had the correct username and password. So I think there may be a problem with transmitting passwords overall. Any ideas?

---

