---
title: "D-Link DWA-643 Xtreme N Express Card Adapter not working after Lucid upgrade"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by Sean Hayes on 2010-05-04
1. D-Link DWA-643 Xtreme N Express Card Adapter
The onboard wireless for my HP tx1000z stopped working a long time ago. This wireless adapter is in my express card slot.

2. 
```
$ lspci
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
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
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
```
I remember my card used to chow up in this list.

```
$ lsusb
Bus 001 Device 006: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 005: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
Hewlett-Packard Wireless is the onboard wireless that hasn't worked in 2 over years.

3.
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:73:87:71  
          inet addr:192.168.10.193  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe73:8771/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22746995 (22.7 MB)  TX bytes:2585404 (2.5 MB)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1300 (1.3 KB)  TX bytes:1300 (1.3 KB)
```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.
```

4.
```
$ lsmod | grep ath9k
ath9k                 278176  0 
mac80211              210008  1 ath9k
led_class               5256  1 ath9k
ath                    10304  1 ath9k
cfg80211              109144  3 ath9k,mac80211,ath
```

5. ```
$ dmesg|grep ath9k
```
Returned nothing.

6. ```
$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

7. ```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```

8. ```
$ lsb_release -d
Description:	Ubuntu 10.04 LTS
```

9. ```
$ uname -mr
2.6.31-19-generic x86_64
```
I'm using an older kernel because I can't boot with the newer ones.

10. ```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                       [ OK ]
```

The ath9k driver appears to load successfully, it looks like the hardware isn't being recognized.

---

### Post by tannalv on 2010-05-06
> **Sean Hayes said:**
> 1. D-Link DWA-643 Xtreme N Express Card Adapter
The onboard wireless for my HP tx1000z stopped working a long time ago. This wireless adapter is in my express card slot.

8. ```
$ lsb_release -d
Description:	Ubuntu 10.04 LTS
```

9. ```
$ uname -mr
2.6.31-19-generic x86_64
```
I'm using an older kernel because I can't boot with the newer ones.

10. ```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                       [ OK ]
```

The ath9k driver appears to load successfully, it looks like the hardware isn't being recognized.

1. [https://help.ubuntu.com/community/ExpressCard]("https://help.ubuntu.com/community/ExpressCard")

[I]Kernel Module

sudo modprobe pciehp pciehp_force=1

In Ubuntu 9.10 this option is compiled in so there is no such module. It is as if the module is always loaded.

To do the equivalent of this last command in Ubuntu 9.10 pass the "pciehp.pciehp_force=1" to the kernel by editing /etc/default/grub file( See Grub2 ). Add it to the line 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
so it appears as 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"

Save and exit your text editor. Then run: 

sudo update-grub

And reboot.[/I]

However, what makes me curious is your problem with newer kernels. What happens? Where does the boot stop? What does it say? I'm sure there is a tx1000 thread for this specific problem. That was a pretty popular laptop, and it still is quiet good.
(Apart from some models having a problem with the GPU heating up/cooling down, leaving cracks in the grid array which, in turns, makes the screen black. Can be moderately easily fixed by pulling motherboard out and heating the GPU area to about 180-200C/300F.)

---

### Post by Sean Hayes on 2010-05-06
> **tannalv said:**
> 1. [https://help.ubuntu.com/community/ExpressCard]("https://help.ubuntu.com/community/ExpressCard")

[I]Kernel Module

sudo modprobe pciehp pciehp_force=1

In Ubuntu 9.10 this option is compiled in so there is no such module. It is as if the module is always loaded.

To do the equivalent of this last command in Ubuntu 9.10 pass the "pciehp.pciehp_force=1" to the kernel by editing /etc/default/grub file( See Grub2 ). Add it to the line 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
so it appears as 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"

Save and exit your text editor. Then run: 

sudo update-grub

And reboot.[/I]

However, what makes me curious is your problem with newer kernels. What happens? Where does the boot stop? What does it say? I'm sure there is a tx1000 thread for this specific problem. That was a pretty popular laptop, and it still is quiet good.
(Apart from some models having a problem with the GPU heating up/cooling down, leaving cracks in the grid array which, in turns, makes the screen black. Can be moderately easily fixed by pulling motherboard out and heating the GPU area to about 180-200C/300F.)

```
$ sudo modprobe pciehp pciehp_force=1
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module pciehp not found.
```

I then edited /etc/default/grub, which was empty, typed in "GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1"", saved it, updated grub, and rebooted. Wireless still isn't recognized, and "sudo modprobe pciehp pciehp_force=1" gives the same error.

With the newer kernels it has a bunch of lines saying something about a parameter name in a config file being deprecated and that it won't be recognized in future versions. Then there's a line saying something like "/dev/sda1: clean, xxxxxxxxx/xxxxxxxxx files, xxxxxxxxxx/xxxxxxxxx blocks" (the x's are numbers). It stops there. If I hit one of the arrow keys I can see the Ubuntu boot screen, but it just stays like that, for hours with no activity.

---

### Post by Sean Hayes on 2010-05-07
All of a sudden it started working again. I wonder if it might be a hardware problem. A few weeks ago it stopped working for a day and then started working again for no reason.

Anyway, I did a fresh install of Lucid and the newer kernels work too.

---

