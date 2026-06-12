---
title: "Very slow download speeds with new 12.04 upgrade"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by adglife on 2012-08-08
Hello Ubuntu world!

I am completely and utterly new, so stick with me here.

I have a desktop computer that I had Ubuntu 10.10 loaded on. Started it up after about a year and upgraded gradually to 12.04 LTS. 

(I want to post specs, but how do I do it in the fancy scroll box?)

Anyway, I have noticed extremely slow internet speeds since day 1. I just got done reading a popular post about MTU and RMEM, etc., and have tried adjusting but I'm afraid I'm completely lost.

Currently purchasing a 1.5M connection (bottom of the totem pole), and average download speeds of .50M down. :( Sometimes far, far less. 

Noticed that interface in use is "lo" not "wlan0". 

Help!

---

### Post by chili555 on 2012-08-08
We want to see your specs. Please post them and highlight them and click the code button. Please see attached.

```
My specs
```Be sure to include:```
lspci -nn | grep -e 0200 -e 0280
lsb_release -d
ping -c3 8.8.8.8
```Thanks.

---

### Post by adglife on 2012-08-08
Ok, specs here:

```
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 2013MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 7
          bus info: cpu@0
          version: 15.11.2
          size: 2500MHz
          capacity: 2500MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP55 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP55 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:e800(size=64) ioport:1c00(size=64) ioport:1c80(size=64)
     *-usb:0
          description: USB controller
          product: MCP55 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fc105000-fc105fff
     *-usb:1
          description: USB controller
          product: MCP55 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fc106000-fc1060ff
     *-ide:0
          description: IDE interface
          product: MCP55 IDE
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          logical name: scsi0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-cdrom
             description: DVD reader
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             capabilities: audio dvd
             configuration: status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:a800(size=8) ioport:ac00(size=4) ioport:b000(size=8) ioport:b400(size=4) ioport:b800(size=16) memory:fc10a000-fc10afff
     *-ide:2
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 5.1
          bus info: pci@0000:00:05.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:bc00(size=8) ioport:c000(size=4) ioport:c400(size=8) ioport:c800(size=4) ioport:cc00(size=16) memory:fc10b000-fc10bfff
     *-ide:3
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 5.2
          bus info: pci@0000:00:05.2
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:d000(size=8) ioport:d400(size=4) ioport:d800(size=8) ioport:dc00(size=4) ioport:e000(size=16) memory:fc104000-fc104fff
     *-pci:0
          description: PCI bridge
          product: MCP55 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
          resources: memory:fc000000-fc0fffff
        *-network
             description: Wireless interface
             product: RT2561/RT61 802.11g PCI
             vendor: Ralink corp.
             physical id: 7
             bus info: pci@0000:01:07.0
             logical name: wlan0
             version: 00
             serial: 00:1c:10:e3:b7:7b
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt61pci driverversion=3.2.0-27-generic firmware=0.8 ip=192.168.2.7 latency=32 multicast=yes wireless=IEEE 802.11bg
             resources: irq:19 memory:fc000000-fc007fff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: a
             bus info: pci@0000:01:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=3
             resources: irq:18 memory:fc00c000-fc00c7ff memory:fc008000-fc00bfff
     *-multimedia
          description: Audio device
          product: MCP55 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 6.1
          bus info: pci@0000:00:06.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:fc100000-fc103fff
     *-bridge
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: eth0
          version: a3
          serial: 00:1d:7d:d7:5a:b7
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:41 memory:fc107000-fc107fff ioport:e400(size=8) memory:fc108000-fc1080ff memory:fc109000-fc10900f
     *-pci:1
          description: PCI bridge
          product: MCP55 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:9000(size=4096) memory:f8000000-fbffffff ioport:e0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G86 [GeForce 8500 GT]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:16 memory:fa000000-faffffff memory:e0000000-efffffff memory:f8000000-f9ffffff ioport:9000(size=128) memory:fb000000-fb01ffff
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

And:

```
anthony@ubuntu:~$ lspci -nn | grep -e 0200 -e 0280
01:07.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]

```

And:

```
Description:	Ubuntu 12.04 LTS

```

And ping

```
anthony@ubuntu:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=48 time=52.7 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=48 time=53.2 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2008ms
rtt min/avg/max/mdev = 52.711/52.981/53.251/0.270 ms

```

---

### Post by chili555 on 2012-08-08
> *-network
             description: Wireless interface
             product: RT2561/RT61 802.11g PCI
             vendor: Ralink corp.
             physical id: 7
             bus info: pci@0000:01:07.0
             logical name: wlan0
             version: 00
             serial: xx:1c:10:e3:b7:xx
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=[COLOR="Red"]rt61pci [/COLOR]driverversion=3.2.0-27-generic firmware=0.8 ip=192.168.2.7 latency=32 multicast=yes wireless=IEEE 802.11bgYour ping times are indeed a bit long. You might try a driver parameter:```
sudo modprobe -r rt61pci
sudo modprobe rt61pci nohwcrypt=Y
```Now check:```
ping -c3 8.8.8.8
```Any improvement?

How is your signal strength?```
nm-tool
```You might also try installing the Ubuntu version of compat-wireless:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic
```You may need the pae version; check:```
uname -r
```If your kernel version is pae, then do:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae
```Reboot and let us hear your report.

---

### Post by adglife on 2012-08-08
> **chili555 said:**
> Reboot and let us hear your report.

I don't have any idea what you just had me do with my computer, but I'm up to exactly where I need to be. Seems to have worked. Can you dumb down what you did so that I can paint the picture in my head of the magic that just happened?

---

### Post by chili555 on 2012-08-08
The compat-wireless project aims to fine-tune and update drivers beyond the vanilla in-kernel version. Often, not always, a correction or improvement is included in compat-wireless. This package is an Ubuntu-ized version: linux-backports-modules-[COLOR="Red"]cw[/COLOR]-3.3-precise-generic.

Or was it the driver parameter that fixed it?```
sudo modprobe rt61pci nohwcrypt=Y
```If so, we'll need to take steps to make it persistent.

---

### Post by adglife on 2012-08-08
Great! Well... how do I make it persistent?

---

### Post by chili555 on 2012-08-09
> **adglife said:**
> Great! Well... how do I make it persistent?Please open a terminal and do:```
sudo gedit /etc/modprobe.d/rt61pci.conf
```A new empty file will open. Please add one line:```
options rt61pci nohwcrypt=Y
```Proofread, save and close gedit. You should be all set.

---

### Post by eldudorinio on 2012-08-21
Hi,

I have recently installed Lubuntu 12.04 (dual boot with Windows XP SP3) on my machine and I've been having similar issues with *adglife*. 
Internet overall quality is much better on Windows XP.

I would follow the above instructions, however since my Ethernet controller is different, I am not quite sure how to modify the commands

Here are my basic system specifications:
```
Processor:	AMD Athlon(tm) 64 Processor 3500+
Memory:	                3016MB (833MB used)
Operating System:	Ubuntu 12.04.1 LTS
OpenGL Renderer:	GeForce GT 630/PCIe/SSE2
Audio Adapter:	        VIA8237 - VIA 8237
Ethernet controller:	Sundance Technology Inc / IC Plus Corp IP1000 Family Gigabit Ethernet (rev 41)
```

Result from lspci -nn | grep -e 0200 -e 0280:
```
00:0e.0 Ethernet controller [0200]: Sundance Technology Inc / IC Plus Corp IP1000 Family Gigabit Ethernet [13f0:1023] (rev 41)
```

Result from lsb_release -d:
```
Description:	Ubuntu 12.04.1 LTS
```

Result from ping -c3 8.8.8.8:
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=49 time=107 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=49 time=106 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=49 time=107 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 106.659/106.983/107.243/0.449 ms
```

Can anyone help?

If any additional information is needed for troubleshooting, please let me know.

Thank you,
Yiannis

---

### Post by chili555 on 2012-08-22
Since your problem is wired and not wireless, the fixes above are not applicable. Would you please start your own new thread?

---

### Post by eldudorinio on 2012-08-22
Absolutely, thanks.

---

