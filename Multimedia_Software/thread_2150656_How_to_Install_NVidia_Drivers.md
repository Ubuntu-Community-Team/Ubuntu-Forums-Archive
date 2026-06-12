---
title: "How to Install NVidia Drivers"
date: 2013-06-01
forum: Multimedia Software
---

### Post by Robert R on 2013-06-01
Hi everyone, 
 i just installed ubuntu on my desktop and have an asus maximus gene v board. It comes with drivers for linux but i dont know how to install them. 

Can anyone have a guide or walktrough ... i also need to install drivers for my video card.. anyone please help much thanks :)

---

### Post by QIII on 2013-06-01
Hello!

What is the make and model of the video card?

---

### Post by Robert R on 2013-06-01
> **QIII said:**
> Hello!

What is the make and model of the video card?

Video card is nvidia gtx 660.

---

### Post by QIII on 2013-06-01
Rather than me trying to reinvent the wheel, you might have a look at [this](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).

If it makes things more confusing, come on back and someone will help you sort it out.

Best wishes!

---

### Post by Sef on 2013-06-01
Moved to M&V.

---

### Post by Yellow Pasque on 2013-06-01
It's nice that Asus pays attention to Linux, but you probably don't need to install those drivers. Can you paste output of:
```
lspci -v
```

---

### Post by Robert R on 2013-06-02
> **Temüjin said:**
> It's nice that Asus pays attention to Linux, but you probably don't need to install those drivers. Can you paste output of:
```
lspci -v
```

The drivers i have are for the MB, chipset etc, i dont have drivers for the videocard im using the defualt but i can tell by the performance of the desktop 
that it needs drivers because the system is a bit sluggish and its  a new install. Also I have ubuntu on my laptop and it works great, because of that
im going to use it permanently on my desktop if i can overcome these hurdles because i cant afford windows software.... anyways 


Here is the output of the command:

tom@Tom-Ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e8000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at f7320000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at f733b000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f7300000 (32-bit, non-prefetchable) [size=128K]
    Memory at f7339000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7338000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84fd
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at f7330000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: e0100000-e02fffff
    Prefetchable memory behind bridge: 00000000e0300000-00000000e04fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f7200000-f72fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 8 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f7100000-f71fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7337000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 48
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f020 [size=32]
    Memory at f7336000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: medium devsel, IRQ 10
    Memory at f7335000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation Device 11c0 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 8423
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nvidia_current_updates, nouveau, nvidiafb

01:00.1 Audio device: NVIDIA Corporation Device 0e0b (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 8423
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>either
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8488
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f7200000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

04:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 84b7
    Flags: bus master, fast devsel, latency 0, IRQ 49
    I/O ports at d050 [size=8]
    I/O ports at d040 [size=4]
    I/O ports at d030 [size=8]
    I/O ports at d020 [size=4]
    I/O ports at d000 [size=32]
    Memory at f7100000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

---

### Post by deadflowr on 2013-06-02
You have video drivers already installed.
The problem is you both nvidia-current and nvidia-current-updates installed, somehow.

see if removing one helps.

---

### Post by Robert R on 2013-06-02
> **QIII said:**
> Rather than me trying to reinvent the wheel, you might have a look at [this]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").

If it makes things more confusing, come on back and someone will help you sort it out.

Best wishes!


After followingt the links it does become confusing for me as i am not sure what to download, however i went to nvidias site and under this link 

[http://www.nvidia.com/object/linux-display-amd64-319.23-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.23-driver.html)

there are linux drivers however the file is a "NVIDIA-Linux-x86_64-319.23.run" file and i have no clue what to do with it. 

it just opens in gedit and looks like code ... do you know what to do with it ??? thanks :)

---

### Post by Robert R on 2013-06-02
> **deadflowr said:**
> You have video drivers already installed.
The problem is you both nvidia-current and nvidia-current-updates installed, somehow.

see if removing one helps.

how do i remove them please ?? also which one should i remove ?

---

### Post by deadflowr on 2013-06-02
You run
```
sudo apt-get remove package
```

change package with either nvidia-current, or nvidia-current-updates.

If problems arise, to reinstall the package use
```
sudo apt-get update
```
and then
```
sudo apt-get install package
```

Again, replace package with whichever nvidia package you choose.

---

### Post by NikTh on 2013-06-02
> **Robert R said:**
> 

01:00.0 VGA compatible controller: NVIDIA Corporation Device 11c0 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 8423
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
    **Kernel driver in use: nvidia**
    Kernel modules: nvidia_current, nvidia_current_updates, nouveau, nvidiafb

The driver seems to be installed and used. Do you have any particular problem ? 

Results might help 

```
apt-cache policy nvidia-*
lspci -nnk | grep -iA2 vga
```

_Please click on **"Reply to Thread"** and put the results between [CODE] tags to be easier to read._ [See here how]("http://i.imgur.com/0hVxL9Q.png")

---

### Post by Yellow Pasque on 2013-06-02
> there are linux drivers however the file is a "NVIDIA-Linux-x86_64-319.23.run" file and i have no clue what to do with it.


Delete it. Use the Ubuntu repo to get drivers when possible (this isn't Windows).

---

### Post by QIII on 2013-06-02
I'm sorry, Robert R!

The link describes how to install the driver from the repository, just as Temüjin has suggested.  I was hoping you *wouldn't *go the NVIDIA site!  :)

---

### Post by Robert R on 2013-06-02
> **NikTh said:**
> The driver seems to be installed and used. Do you have any particular problem ? 

Results might help 

```
apt-cache policy nvidia-*
lspci -nnk | grep -iA2 vga
```

_Please click on **"Reply to Thread"** and put the results between ```
 tags to be easier to read._ [See here how]("http://i.imgur.com/0hVxL9Q.png")

HI Here is the output from the code, the problem im having is that the system behaves as though there are no vide drivers installed... example tearing while scrolling through web pages etc.. 

[CODE]tom@Tom-Ubuntu:~$ apt-cache policy nvidia-*
nvidia-vdpau-driver:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-cuda-profiler:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-173-dev:
  Installed: (none)
  Candidate: 173.14.35-0ubuntu0.2
  Version table:
     173.14.35-0ubuntu0.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
     173.14.30-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-common:
  Installed: 1:0.2.44.2
  Candidate: 1:0.2.44.2
  Version table:
 *** 1:0.2.44.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:0.2.44 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
nvidia-libopencl1:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-173:
  Installed: (none)
  Candidate: 173.14.35-0ubuntu0.2
  Version table:
     173.14.35-0ubuntu0.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
     173.14.30-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-cg-toolkit:
  Installed: (none)
  Candidate: 3.0.0016-0ubuntu1
  Version table:
     3.0.0016-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages
nvidia-current:
  Installed: 304.88-0ubuntu0.0.2
  Candidate: 304.88-0ubuntu0.0.2
  Version table:
 *** 304.88-0ubuntu0.0.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-experimental-310-dev:
  Installed: (none)
  Candidate: 310.14-0ubuntu0.3
  Version table:
     310.14-0ubuntu0.3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
nvidia-96:
  Installed: (none)
  Candidate: 96.43.23-0ubuntu0.1
  Version table:
     96.43.23-0ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
     96.43.20-0ubuntu6 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-96-updates:
  Installed: (none)
  Candidate: 96.43.20-0ubuntu5
  Version table:
     96.43.20-0ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-glx-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-current-modaliases:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-vdpau-driver-ia32:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-173-updates:
  Installed: (none)
  Candidate: 173.14.36-0ubuntu0.0.1
  Version table:
     173.14.36-0ubuntu0.0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
     173.14.35-0ubuntu0.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
     173.14.30-0ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-va-driver:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-libvdpau:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-current-updates:
  Installed: 304.88-0ubuntu0.0.1
  Candidate: 304.88-0ubuntu0.0.1
  Version table:
 *** 304.88-0ubuntu0.0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-tegra:
  Installed: (none)
  Candidate: (none)
  Version table:
boinc-nvidia-cuda:
  Installed: (none)
  Candidate: 7.0.27+dfsg-5ubuntu0.12.04.1
  Version table:
     7.0.65+dfsg-3~ubuntu12.04.1 0
        100 http://us.archive.ubuntu.com/ubuntu/ precise-backports/multiverse amd64 Packages
     7.0.27+dfsg-5ubuntu0.12.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse amd64 Packages
     7.0.24+dfsg-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages
nvidia-opencl-profiler:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-opencl-dev:
  Installed: (none)
  Candidate: 4.0.17-3ubuntu0.1
  Version table:
     4.0.17-3ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse amd64 Packages
nvidia-opencl-icd:
  Installed: (none)
  Candidate: (none)
  Version table:
libgl1-nvidia-alternatives:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-settings-updates:
  Installed: 304.88-0ubuntu0.0.2
  Candidate: 304.88-0ubuntu0.0.2
  Version table:
 *** 304.88-0ubuntu0.0.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
        100 /var/lib/dpkg/status
     295.33-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-96-dev:
  Installed: (none)
  Candidate: 96.43.23-0ubuntu0.1
  Version table:
     96.43.23-0ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
     96.43.20-0ubuntu6 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-96-updates-dev:
  Installed: (none)
  Candidate: 96.43.20-0ubuntu5
  Version table:
     96.43.20-0ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-180-modaliases:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-cuda-dev:
  Installed: (none)
  Candidate: 4.0.17-3ubuntu0.1
  Version table:
     4.0.17-3ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse amd64 Packages
nvidia-cuda-doc:
  Installed: (none)
  Candidate: 4.0.17-3ubuntu0.1
  Version table:
     4.0.17-3ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse amd64 Packages
nvidia-cuda-gdb:
  Installed: (none)
  Candidate: 4.0.17-3ubuntu0.1
  Version table:
     4.0.17-3ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse amd64 Packages
nvidia-173-updates-dev:
  Installed: (none)
  Candidate: 173.14.36-0ubuntu0.0.1
  Version table:
     173.14.36-0ubuntu0.0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
     173.14.35-0ubuntu0.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
     173.14.30-0ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-current-updates-dev:
  Installed: (none)
  Candidate: 304.88-0ubuntu0.0.1
  Version table:
     304.88-0ubuntu0.0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-96-modaliases:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-cuda-toolkit:
  Installed: (none)
  Candidate: 4.0.17-3ubuntu0.1
  Version table:
     4.0.17-3ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse amd64 Packages
nvidia-libvdpau-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-libvdpau-ia32:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-cuda-debugger:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-libopencl1-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-settings-experimental-304:
  Installed: (none)
  Candidate: 304.48-0ubuntu0.1
  Version table:
     304.48-0ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
nvidia-settings-experimental-310:
  Installed: (none)
  Candidate: 310.14-0ubuntu0.1
  Version table:
     310.14-0ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
nvidia-libvdpau1:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-libvdpau1-ia32:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-compute-profiler:
  Installed: (none)
  Candidate: 4.0.17-3ubuntu0.1
  Version table:
     4.0.17-3ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse amd64 Packages
nvidia-current-dev:
  Installed: (none)
  Candidate: 304.88-0ubuntu0.0.2
  Version table:
     304.88-0ubuntu0.0.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-173-modaliases:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-304-dev:
  Installed: (none)
  Candidate: 304.48-0ubuntu0.1
  Version table:
     304.48-0ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
nvidia-185-modaliases:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-glx:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-304:
  Installed: (none)
  Candidate: 304.48-0ubuntu0.1
  Version table:
     304.48-0ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
libkwinactivenvidiahack4:
  Installed: (none)
  Candidate: 4:4.8.5-0ubuntu0.3
  Version table:
     4:4.8.5-0ubuntu0.3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
     4:4.8.2a-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
nvidia-experimental-310:
  Installed: (none)
  Candidate: 310.14-0ubuntu0.3
  Version table:
     310.14-0ubuntu0.3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
nvidia-settings:
  Installed: 304.88-0ubuntu0.0.2
  Candidate: 304.88-0ubuntu0.0.2
  Version table:
 *** 304.88-0ubuntu0.0.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
        100 /var/lib/dpkg/status
     295.33-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
nvidia-texture-tools:
  Installed: (none)
  Candidate: (none)
  Version table:
libkwinnvidiahack4:
  Installed: (none)
  Candidate: 4:4.8.5-0ubuntu0.3
  Version table:
     4:4.8.5-0ubuntu0.3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
     4:4.8.2a-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
tom@Tom-Ubuntu:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:11c0] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8423]
    Kernel driver in use: nvidia


```

---

### Post by NikTh on 2013-06-02
Try 
```
sudo apt-get purge nvidia-*
sudo rm /etc/X11/xorg.conf
[COLOR=#3C3B37][FONT=Monaco]sudo apt-get purge $(dpkg -l | awk '/^rc/ { print $2 }')[/FONT][/COLOR]
sudo apt-get install --reinstall xserver-xorg-video-nouveau 
sudo dpkg-reconfigure xserver-xorg
``` 

Then 
```
sudo apt-get update ; sudo apt-get dist-upgrade
sudo apt-get install nvidia-experimental-310 nvidia-settings-experimental-310 
sudo nvidia-xconfig
``` 

Reboot your PC.

---

### Post by Robert R on 2013-06-02
After Many attempts this is the results:

Even throught the repositories i get the following error:


[ATTACH=CONFIG]243438[/ATTACH]

I Did check the dependencies option it is fine.. im just unable to get the sstem to see my video card...

anmore help is appreciated 

so far 

I installed GDM cant stop the service because it says GDM or GDM3 not found so i cant install the run files.
the repositories install just fails... not sure where to go from here ? 

[ATTACH=CONFIG]243436[/ATTACH][ATTACH=CONFIG]243437[/ATTACH]

---

### Post by NikTh on 2013-06-02
The "Graphics: Unknown" is not a big deal. Just install mesa-utils and it will recognize your graphics card 
```
sudo apt-get install mesa-utils
```. 

But it would be helpful if you post the full terminal results. 

```
dpkg -l | grep -i nvidia 
sudo apt-get update 
find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```

---

### Post by Yellow Pasque on 2013-06-02
Sigh... Again (and for the last time), delete the .run file. If you want nvidia 319.23 driver, you can use xorg-edgers ppa, where it's already packaged. [https://launchpad.net/~xorg-edgers/+archive/ppa/+index?field.series_filter=raring](https://launchpad.net/~xorg-edgers/+archive/ppa/+index?field.series_filter=raring)

---

### Post by Robert R on 2013-06-16
> **Temüjin said:**
> Sigh... Again (and for the last time), delete the .run file. If you want nvidia 319.23 driver, you can use xorg-edgers ppa, where it's already packaged. [https://launchpad.net/~xorg-edgers/+archive/ppa/+index?field.series_filter=raring](https://launchpad.net/~xorg-edgers/+archive/ppa/+index?field.series_filter=raring)

I have added them to the repositories and installed their drivers, Ubuntu crashed and after a week of troubleshooting i cant get it to load. ](*,)

So today im installing  it all over again and thank god i had things backed up. So i guess its back to the drawing board with this issue.

---

### Post by Robert R on 2013-06-16
> **NikTh said:**
> The "Graphics: Unknown" is not a big deal. Just install mesa-utils and it will recognize your graphics card 
```
sudo apt-get install mesa-utils
```. 

But it would be helpful if you post the full terminal results. 

```
dpkg -l | grep -i nvidia 
sudo apt-get update 
find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```

Although i cant post the results of this command as my system has crashed and is being redone i will once its back up and running. 
Hopefully it may provide some insight into something that may help somebody else with this graphics card. 

If you have any other ideas though im all ears. ;)

---

### Post by NikTh on 2013-06-16
> **Robert R said:**
> 
So today im installing  it all over again and thank god i had things backed up. So i guess its back to the drawing board with this issue.

> **Robert R said:**
> Although i cant post the results of this command as my system has crashed and is being redone i will once its back up and running. 
Hopefully it may provide some insight into something that may help somebody else with this graphics card. 

If you have any other ideas though im all ears. ;)

If you re-installed Ubuntu then the results does not matter. 

Please close this thread as SOLVED, although I'm not a fan of re-installations in Linux. 

See my signature on a How To mark the thread as solved. 

Regards 
 NikTh

---

### Post by wc711 on 2013-06-17
I had the same problem on my third installation.  I couldn't even reboot because I got a screen that said I had a graphics problem.  I selected the trouble shoot option and got the terminal.  I couldn't really understand what I was looking at, but towards the very end I read a line that stated the Nvidia driver couldn't be intalled because there was already one installed. I had now way of knowing how to uninstall one and install the new.  On the installation from the DVD I found the "additional drivers" icon and clicked it.  I got the screen that showed 3 Nvidia drivers.  I activated all 3, rebooted and had a good screen. The next time I dicided to go with a side by side installation.  This time there were no dirvers in the additional driver screen so I went to Nvidia and downloaded the driver and installed il with wine program.  It worked and I proceeded with the setup.  The problem there was I got a notification that there were almost 300 updates that needed to be installed. 

I started that process and eventually was told that there wasn't enough disk space which was impossible because I have a 500 gig hd.  I did an uninstall after hours of trying to make it work.  The next time I did an install with Penn Drive for Linux. It enable me to partition my hard drive and install 13.04.  I choose that one because I didn't want to mix it up with the 12.01 that was having all the problems.  Before installing Ubuntu uninstalled all the old files.  The Nvidia problem was still there, but the additional driver icon, which I had to search for because it wasn't on the launch bar,  got me the Nvidia driver screen.  This one was more legible and the descriptions were better.  I still wasn't sure which one to choose so I started with the last one in line and it turned out to be not compatible with my system so I went up to the next one and it was.  I rebooted and everything is fine (so far), but since I have all the software I want and all my pictures, video and music files transferred, I'm good to go.  The updates and software are installed with the OS install so you don't have to worry about that.

---

