---
title: "Can't Connect to Internet"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by cvan84 on 2009-10-13
I replied to this in another thread but figured I'd go ahead and start my own. I just installed Ubuntu last night and can't get it to connect to anything. 
I typed in 2 things in the terminal that I saw in another thread

**sudo lshw -C network**

*network
description: Network Controller
poduct: BCM4328 802.11a/b/g/n
vendor:Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 03
width 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap list
Config: driver=b43-pci-bridge latency=0 module=ssb

*network DISABLED
description: Ethernet interface
physical id: 1
logical name pan0
serial: 0e:97:c2:ad:3d:cd
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


The other thing:

**sudo iwconfig scan**
scan No such device


The Network Manager (the 4 bars at the top right) has a red x on the icon. when I right click, Enable Networking is checked. My wireless button on my keyboard is also ON. 

When I goto Hardware Drivers, Broadcom STA wireless driver is Enabled. It also says this driver is activated but not currently in use

I have tried restarting the computer, also. 

Any help would be much appreciated. 
Thanks

---

### Post by bkratz on 2009-10-13
> **cvan84 said:**
> I replied to this in another thread but figured I'd go ahead and start my own. I just installed Ubuntu last night and can't get it to connect to anything. 
I typed in 2 things in the terminal that I saw in another thread
.
.
.

Any help would be much appreciated. 
Thanks


Have a look at this thread, it may help .

[http://ubuntuforums.org/showthread.php?t=1257311](http://ubuntuforums.org/showthread.php?t=1257311)


Good Luck

---

### Post by shredder12 on 2009-10-13
How are you trying to connect to internet??
wireless or wired..

if wireless then check whether the wireless switch is on and if there are some wireless networks then left-clicking on the network manager should show them..

---

### Post by cvan84 on 2009-10-13
Wireless
yes the switch is on, but no networks are showing

---

### Post by shredder12 on 2009-10-13
please make sure that wireless networks are available. Try connecting using another computer or windows.
and post the outputs of 
```
lspci
```
```
sudo iwconfig
```
```
sudo iwlist scanning
```

---

### Post by cvan84 on 2009-10-13
> **shredder12 said:**
> please make sure that wireless networks are available. Try connecting using another computer or windows.
and post the outputs of 
```
lspci
```
```
sudo iwconfig
```
```
sudo iwlist scanning
```

Wireless connections are available. I'm on my Windows laptop as we speak.
here are the outputs:

**lspci**
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

**sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:14 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-57 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**sudo iwlist scanning**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:0E:46:43:03
                    ESSID:"WEST1014"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-68 dBm  Noise level:-88 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:18:F8:AC:B9:AF
                    ESSID:"HomeOffice"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-88 dBm  Noise level:-87 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:22:3F:7D:5B:5E
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-55 dBm  Noise level:-88 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:18:4D:7D:18:FA
                    ESSID:"Airman"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s




Thanks for everyone's help btw. Even though I'm a huge noob right now, I look forward to learning more about this OS

---

### Post by cvan84 on 2009-10-13
Got it!
tried this from the other thread:
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
echo wl | sudo tee -a /etc/modules

and it worked

Thanks a lot :)

---

### Post by shredder12 on 2009-10-13
YOu can see from the result of iwlist scanning that you are able to scan the available networks..
I don't understand why won't your network manager show it.
try installing wifi-radar..
```
sudo apt-get install wifi-radar
```
It helps in managing your wireless networks. It should work. If it doesn't work too. then you may try installing wicd..
```
sudo apt-get install wicd
```

I am not sure about your NM problem that's why I am suggesting you to use other applications to handle your network connections. Buy you may want to wait for a while and see if someone suggests a fix for ur problem.

---

