---
title: "Network suddenly not working."
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by psmaster on 2009-07-17
I was installing the ATI fglrx drivers using Envy, that did not turn out to be a good idea, so I uninstalled those and installed the 9.4 version of the driver. Now I do not have network activity. It is not my network, because it does the same thing on all the networks around me I try to connect to. Here is the output of my lspci:

```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f4)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
05:07.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
05:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
05:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

If you want to see certain logs, contact me.
Any help is appreciated!

---

### Post by aesis05401 on 2009-07-17
> **psmaster said:**
> 05:07.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


Unless this line is showing an adapter you don't recognize it looks like it is there. 

So can you do an ifconfig and post the output?  Please include a brief description of how you think the LANs you connect to are set up ie: DHCP, WPA(2), etc...

---

### Post by psmaster on 2009-07-17
> **aesis05401 said:**
> Unless this line is showing an adapter you don't recognize it looks like it is there. 

So can you do an ifconfig and post the output?  Please include a brief description of how you think the LANs you connect to are set up ie: DHCP, WPA(2), etc...

Hold on, I am on a live CD, so I will have to restart to do get any data that might help

---

### Post by aesis05401 on 2009-07-17
Wait!! If you are on the livecd and net access is working then copy whatever info ifconfig or iwconfig shows about the state of your adapters.  

Once you reboot into the old install compare the ifconfig info from live cd with what you see on old install.

Then check your /etc/network/interfaces file to see if there are commands in there causing your default settings to be changed to something unworkable.  If you think something funny is in the interfaces text file then post that as well.

---

### Post by psmaster on 2009-07-17
Well, I am looking at both of the files, one on the live-cd and the one on my current install and they both look the same. Here is my ifconfig from my current install:

```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:bd:96:ed  
          inet addr:192.168.0.198  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:febd:96ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2211 (2.2 KB)  TX bytes:1773 (1.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-95-BD-96-ED-36-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

And here is the ifconfig from the live-cd

```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:bd:96:ed  
          inet addr:192.168.0.198  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:febd:96ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18767890 (18.7 MB)  TX bytes:1144146 (1.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-95-BD-96-ED-36-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

The /etc/network/interfaces file seems to be the same on both
```

auto lo
iface lo inet loopback

```

*EDIT:
After viewing some of the logs, I believe it might be an issue with the driver. The driver in use is ath5k
I have uploaded my dmesg log and my kern.log to all who care to see at [http://www.reelone.org/psmaster/dmesg.txt](http://www.reelone.org/psmaster/dmesg.txt)
[http://www.reelone.org/psmaster/kernlog.txt](http://www.reelone.org/psmaster/kernlog.txt)

---

