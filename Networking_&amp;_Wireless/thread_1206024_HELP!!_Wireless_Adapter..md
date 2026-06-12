---
title: "HELP!! Wireless Adapter."
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by scottj72 on 2009-07-06
First let me say I am completely new to Linux and Ubuntu. I thought I would give it a go since I will be making a career cahnge and starting in a graduate transition program.
 
Ok.. so the problem. I have a machine with an AMD 64 X2 dual core processor. I have installed Ubentu 9.04 using Wubi along with Vista. I have no way to access the internet while I use Unbuntu. I have a Linksys WUB300N wirless adapter. I tried usingndiswrapper to load the drivers. But when I enter *sudo ndiswrapper -l* it tells me invalid drivers. I have tried to install the drivers again, but it will tell me the drivers are already installed.
 
I am at a complete loss of even how to procede. Maybe I should uninstall? If so how do i do that? It is becoming very frustrating. It just does not seem it should be this difficult.
 
Thanks

---

### Post by Sankou on 2009-07-06
The first thing you need to do is find the windows driver for the wireless card. If ndiswrapper tells you it's invalid, then it's the wrong driver or the location of the .inf driver does not contain the proper .sys file as well. Once you have the .inf. and .sys files, put them in the same folder. Run this to remove the old driver-

```
sudo ndiswrapper -r [Driver Name] 
```Then try to install the driver again and post the results of _sudo ndiswrapper -l_ and also _lshw -C Network_

---

### Post by Idefix82 on 2009-07-06
What is the output if you type in the terminal
```
lspci
lshw -C network
```

---

### Post by scottj72 on 2009-07-06
Ok. I deleted the driver. I added two .SYS files to the folder with the  .inf file. Loaded driver again. Then put in the other commands you mentioned. Adapter still is not active not lighting up or anything, but looks like the driver is installed now.
 
[EMAIL="scottj72@ubuntu:~$"]scottj72@ubuntu:~$[/EMAIL] sudo ndiswrapper -l
netmw245 : driver installed
 device (13B1:0029) present
 
[EMAIL="scottj72@ubuntu:~$"]scottj72@ubuntu:~$[/EMAIL] lshw -C Network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:41:83:a3:59:39
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Sankou on 2009-07-06
Good, it's a easy fix from there. When you run the command lshw -C Network, it tells you a lot of information about your network devices. The key here is that it tells you what driver is in use by the device. 

> 
scottj72@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:41:83:a3:59:39
       capabilities: ethernet physical
       configuration: broadcast=yes _**driver=bridge**_ driverversion=2.3 firmware=N/A multicast=yes
I don't think this is the wireless device you're trying to get to work though. It should mention wireless or 802.11 somewhere. Run just _lshw_ and search for the wireless in there, It should mention your model number and everything. 

Once you find it, check what driver is being used. If it doesn't say driver=ndiswrapper+[YOUR DRIVER] then blacklist the driver that's mentioned. For example, when I run lshw -C Network, the second device from the bottom is this:
```

*-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 02
       serial: 00:16:01:7d:23:25
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes **driver=ndiswrapper+usrmaxg** driverversion=1.5

```After description it says Wireless Interface. Your device should say the same.

To blacklist a driver, run this:
```

sudo gedit /etc/modprobe.d/blacklist.conf

```Ad a line like this:
Blacklist [inset unwanted driver here]

And then save the file.  After that, run this command:
```

sudo update-initramfs -k all -u

```Now reboot your computer. Everything should work fine.

---

### Post by scottj72 on 2009-07-06
Still not sure what to do to get wireless connection.
 
lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Communication controller: Conexant Systems, Inc. Device 2f81 (rev 01)
 
lsusb
Bus 001 Device 003: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 001 Device 002: ID 13b1:0029 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by scottj72 on 2009-07-06
lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 894MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
          size: 2300MHz
          capacity: 2300MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: [EMAIL="pci@0000:00:00.0"]pci@0000:00:00.0[/EMAIL]
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: [EMAIL="pci@0000:00:01.0"]pci@0000:00:01.0[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: [EMAIL="pci@0000:00:01.1"]pci@0000:00:01.1[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: [EMAIL="pci@0000:00:01.2"]pci@0000:00:01.2[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: [EMAIL="pci@0000:00:02.0"]pci@0000:00:02.0[/EMAIL]
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: [EMAIL="pci@0000:00:02.1"]pci@0000:00:02.1[/EMAIL]
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: [EMAIL="pci@0000:00:04.0"]pci@0000:00:04.0[/EMAIL]
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: [EMAIL="pci@0000:00:05.0"]pci@0000:00:05.0[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: [EMAIL="pci@0000:00:06.0"]pci@0000:00:06.0[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: [EMAIL="pci@0000:00:07.0"]pci@0000:00:07.0[/EMAIL]
          logical name: eth0
          version: a2
          serial: 00:23:54:03:31:d1
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: [EMAIL="pci@0000:00:08.0"]pci@0000:00:08.0[/EMAIL]
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: [EMAIL="pci@0000:00:09.0"]pci@0000:00:09.0[/EMAIL]
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: [EMAIL="pci@0000:00:0b.0"]pci@0000:00:0b.0[/EMAIL]
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
        *-communication UNCLAIMED
             description: Communication controller
             product: Conexant Systems, Inc.
             vendor: Conexant Systems, Inc.
             physical id: 0
             bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
     *-display UNCLAIMED
          description: VGA compatible controller
          product: GeForce 6150SE nForce 430
          vendor: nVidia Corporation
          physical id: d
          bus info: [EMAIL="pci@0000:00:0d.0"]pci@0000:00:0d.0[/EMAIL]
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: latency=0
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: [EMAIL="pci@0000:00:18.0"]pci@0000:00:18.0[/EMAIL]
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: [EMAIL="pci@0000:00:18.1"]pci@0000:00:18.1[/EMAIL]
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: [EMAIL="pci@0000:00:18.2"]pci@0000:00:18.2[/EMAIL]
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: [EMAIL="pci@0000:00:18.3"]pci@0000:00:18.3[/EMAIL]
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-scsi
       physical id: 1
       bus info: [EMAIL="scsi@4"]scsi@4[/EMAIL]
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 52:34:b7:06:5a:2b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by scottj72 on 2009-07-06
hmm ok... i am not seeing the wireless adapter on the list. It did list it when I did isusb but not seeing it in lshw.

---

### Post by Sankou on 2009-07-06
Hmmm.... that's odd that it's not showing up on the list. Try this:

```

sudo modprobe ndiswrapper

```

Then check to see if it is on the list when you type lshw -C Network.

If all else fails, use this guide, it's very helpful!

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by scottj72 on 2009-07-06
got this from that command.
 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
 
Still not listed on lshw or lshw -c network.
Thanks for giving it a go.

---

### Post by scottj72 on 2009-07-06
hmm... after looking at that page I may know what the issue is. I used the drivers from the original CD. I am pretty sure they are 32 bit... I have a 64 bit ubuntu.. going to try and uninstall and find some 64 bit drivers.

---

### Post by scottj72 on 2009-07-06
Still no luck! I tried the most recent drivers from linksys sight. both vista and xp. Still get the same thing. This is crazy. I want to start using and getting familar with linux, but not sure how much I actually will if i can even get my wireless connection so I can have internet.

---

### Post by Sankou on 2009-07-06
The wireless card may not be compatible with ubuntu 64 bit. If the troubleshooting guide I gave you the link to doesn't work, then I would switch to 32 bit.

---

### Post by scottj72 on 2009-07-07
Ok.. an update for any others that may have similar problems. So I uninstalled the Wubi-Ubuntu 64 bit. I then went ahead did the complete dual boot setup with Ubuntu 32 bit and Vista without using Wubi. Installed  ndiswrapper and utilities. Installed drivers. And now finally I have Ubuntu recognizing my adapter. No connection yet, but now I have to figure out where to go next.
 
[EMAIL="cott@scott-desktop:~$"]cott@scott-desktop:~$[/EMAIL] sudo lshw -c network
  *-network:0 DISABLED    
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:d9:10:9e:ff:c7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:70:38:bd:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.53+Linksys, A Division of Cisc link=no multicast=yes wireless=IEEE 802.11g

---

### Post by scottj72 on 2009-07-08
Wow. Starting to really suck. Ok.  made progress... it lights up and blinks from time to time.. but I have not found a way to actually locate or configure.
 
[EMAIL="cott@scott-desktop:~$"]cott@scott-desktop:~$[/EMAIL] sudo lshw -c network
  *-network:0 DISABLED    
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:41:14:e3:c1:35
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:70:38:bd:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.53+Linksys, A Division of Cisc link=no multicast=yes wireless=IEEE 802.11g
[EMAIL="scott@scott-desktop:~$"]scott@scott-desktop:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[EMAIL="scott@scott-desktop:~$"]scott@scott-desktop:~$[/EMAIL]

---

### Post by scottj72 on 2009-07-08
OMG!!! I do not think I have ever worked soo hard and been soo frustrated trying to get some little adapter that plugs into a USB to work. But I am very happy to say that I am now connected and replying  under the Ubuntu operating system.

 I went through a process of trial and error with several different versions of drivers for my adapter. Each time I seemed to get closer, but always noticed the lights on the adapter just did not act the way they did in Vista and I could not connect. 

Finally, I went back to the orginal drivers from the CD....viola...the lights light up the way they were supposed to. I rebooted... imediately it identified the network...I entered my key...and here I am. just incase anyone cares. I just thought I would make note. Maybe it will provide some assistance to somone.

---

