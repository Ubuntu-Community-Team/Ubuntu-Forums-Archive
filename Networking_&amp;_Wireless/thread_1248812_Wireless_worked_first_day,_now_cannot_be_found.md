---
title: "Wireless worked first day, now cannot be found"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by OrangeCrush112 on 2009-08-24
So, I just set up a Toshiba Satellite with Ubuntu 9.04. The first day, I got the wireless up and running after turning on the madwifi driver.
However, on the next day I turn on my laptop and the computer will no longer even see any wireless networks. Wired works fine, however.

The night before it went out, I installed kubuntu-desktop; perhaps this could be related?

```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:18:af:d5  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe18:afd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1629686 (1.6 MB)  TX bytes:259873 (259.8 KB)
          Interrupt:252 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3360 (3.3 KB)  TX bytes:3360 (3.3 KB)

```
Those are the results of running ifconfig. Iwconfig gives me nothing ("no wireless extensions").

Suggestions?

---

### Post by Crafty Kisses on 2009-08-24
Do you know if you took any kernel updates? If you did you're going to have to recompile the drivers. What are the results of the following commands?
```
lspci
lsusb
lshw -C network
```

---

### Post by OrangeCrush112 on 2009-08-24
lspci:
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

lsusb:
```
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lshw
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:18:af:d5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.107 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:9e:34:93:f4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 06:de:53:59:6e:cf
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

I don't believe I had any kernel updates, but I could have done an update and not noticed, or it snuck in during the kubunt-desktop install.

---

### Post by Crafty Kisses on 2009-08-26
Alright, so this is the wireless card you have: ```
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```
Now I'm pretty sure if you compile compat-wireless it should work. So first thing is first, you need to grab the latest version of compat-wireless right **[here.]("http://linuxwireless.org/en/users/Download/stable/")** Once you have grabbed that you need to make sure you have the build-essential package installed, if you don't run the following as root:
```
apt-get install build-essential
```
So now you have the file and build-essential installed, let's compile this. First you need to navigate to your desktop so I'm just guessing you saved it to your desktop so run:
```
cd /home/username/Desktop
```
Where it says username replace it with your username, remember case sensitive. Then you need to run:
```
tar xvjf compat-wireless-2.6*
```
Then there should be an actual compat-wireless folder now, navigate to it, then you can run:
```
make
sudo make install
```
If the compilation doesn't go well, or the driver doesn't work you can always unload the driver by running:
```
make uninstall
```
Reboot by running the following:
```
sudo shutdown -r now
```
Then see if it works.

---

### Post by OrangeCrush112 on 2009-08-30
Nope, that didn't seem to do the trick.

---

### Post by OrangeCrush112 on 2009-08-31
I'm gonna bump this.

A note; you're instructions didn't say to 'make unload.' I didn't do this the first time I installed package, but I did after I uninstalled and reinstalled, and it gave me an error message.

Also, I downloaded wicd manager if that effects anything.

---

### Post by OrangeCrush112 on 2009-09-03
bumping once again.

Please, I really need help, I still have made zero headway into fixing it and am damn near ready to just reinstall the entire OS.

---

