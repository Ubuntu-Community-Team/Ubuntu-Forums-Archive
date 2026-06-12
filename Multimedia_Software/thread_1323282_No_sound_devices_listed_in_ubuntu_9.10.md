---
title: "No sound devices listed in ubuntu 9.10"
date: 2009-11-11
forum: Multimedia Software
---

### Post by Fritzendugan on 2009-11-11
*EDIT* : I'm fairly certain that my sound card (ICH8 family) is just simply not supported under ASLA yet. If anyone feels they know something to the contrary, please let me know.

Firstly, I'm new to the Linux scene, Ubuntu is my first distro, so excuse my novice experience.

Onto my issue, I recently did a fresh install (from the a burned disc using the iso on the page) of a 9.04 version I had. I'm not sure if I had sound at this point as I didn't check, as soon as I got that version up and running I did an upgrade to 9.10 from the upgrade manager. After that, rebooted, and got Ubuntu up and running. Lo and behold, no sound! Went to system->preferences->sound and there are no devices listed under hardware. Tried using LordRaiden's Comprehensive sound solution guide (v0.5e) and I'm fairly certain I followed his steps correctly up to the Alsa Driver compilation part, but I got an error when trying to do
 ```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.28-11-generic

```here is some output from lspci -v
lspci -v
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f4000000-f6ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1800 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at f7504800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f7500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0000000-f3ffffff
    Prefetchable memory behind bridge: 00000000f8000000-00000000f9ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f7100000-f71fffff
    Prefetchable memory behind bridge: 00000000c2000000-00000000c20fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Memory behind bridge: f7200000-f72fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7504c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=10, sec-latency=32
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: f7000000-f70fffff
    Prefetchable memory behind bridge: 00000000c4000000-00000000c7ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18a0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2298
    I/O ports at 18d8 [size=8]
    I/O ports at 18cc [size=4]
    I/O ports at 18d0 [size=8]
    I/O ports at 18c8 [size=4]
    I/O ports at 18e0 [size=32]
    Memory at f7504000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: medium devsel, IRQ 5
    Memory at c2100000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 1c00 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8700M GT] (rev a1)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 2297
    I/O ports at 4000 [size=256]
    Memory at f7100000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at c2000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
    Subsystem: Intel Corporation Device 1100
    Flags: bus master, fast devsel, latency 0, IRQ 2296
    Memory at f7200000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at f7004000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=0c, secondary=0d, subordinate=10, sec-latency=176
    Memory window 0: c4000000-c7fff000 (prefetchable)
    Memory window 1: c8000000-cbfff000
    I/O window 0: 00005000-000050ff
    I/O window 1: 00005400-000054ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, medium devsel, latency 32, IRQ 17
    Memory at f7006000 (32-bit, non-prefetchable) [size=2K]
    Memory at f7000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Toshiba America Info Systems Device ff03
    Flags: bus master, medium devsel, latency 57, IRQ 18
    Memory at f7005000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
    Subsystem: Toshiba America Info Systems Device ff03
    Flags: bus master, medium devsel, latency 57, IRQ 18
    Memory at f7006800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

```I think my sound card is the 82801H HD audio controller. My laptop is a Toshiba Satellite X205-S9810.
 [http://www.newegg.com/Product/Product.aspx?Item=N82E16834114471](http://www.newegg.com/Product/Product.aspx?Item=N82E16834114471)
There's a link to a newegg page of the model of laptop I have.

Hope you guys can help :)

---

### Post by sauma on 2009-11-12
I'm having the same problem. Please help!

---

### Post by cutesolutions on 2009-11-12
I've got exactly the same problem, but the strange thing is that some times the sound works and most of the time not. When i am connected to the internet by cable it never works, with wifi only some times. If i boot with the live cd the sound works. I hope somebody can help. Thanks!

---

### Post by moodle on 2009-11-12
I've also got no sound since I updated to Ubuntu 9.10.  Very frustrating.

I've tried this solution:

[http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala](http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala)

but it didn't work.

My audio output device is listed as 'dummy output'.

Audio worked fine in Ubuntu 9.04.

Please help!

---

### Post by adykhu55 on 2009-11-12
I have the same problem on a Sony Vaio PCG-7f1L.  "Dummy Output" is all that's listed.

And I am *trying* to install alsa, or make sure it's there, but I am sort of clueless with that and having difficulties.  alsa-project.org seems like it hasn't been updated in a while and isn't very beginner-user-friendly (nothing against them, I am just confused).

Wierdly, sound output works in gOS on the same PC that I have installed on another partition!

---

### Post by /G\ on 2009-11-12
Same problem here...I've been trying and trying every 'solution' I could find and nothing would work...It was first giving me a dummy device, and then no device...Now, when I go to System -> Preferences -> Sound, it gives me a box that says "Waiting for sound system to respond"

---

### Post by briml3y on 2009-11-12
I had a sound problem when I upgraded my installation from 9.04 to 9.10 on my dell m1330. I had noticed that when grub booted it loaded a kernal from 9.04. In the end I upgraded to grub 2 and updated the kernal list and everything worked fine as far as sound goes.

I dont remember the link but try upgrading to grub 2 theres plenty of tutorials out there

---

### Post by jgkellt001 on 2009-11-12
> **briml3y said:**
> I had a sound problem when I upgraded my installation from 9.04 to 9.10 on my dell m1330. I had noticed that when grub booted it loaded a kernal from 9.04. In the end I upgraded to grub 2 and updated the kernal list and everything worked fine as far as sound goes.

I dont remember the link but try upgrading to grub 2 theres plenty of tutorials out there

I had same problem with no sound after upgrade from 9.04 to 9.10.Also the burn function was not working properly. Eventually i backed up all my data and did a fresh install, which was a pain, but once I'd reinstalled Flash 10, printer drivers, medibuntu and a few other bits I found everything to be tickity boo and everything now works fine!
 
Regards

jgkellt001

---

### Post by /G\ on 2009-11-12
> **briml3y said:**
> I had a sound problem when I upgraded my installation from 9.04 to 9.10 on my dell m1330. I had noticed that when grub booted it loaded a kernal from 9.04. In the end I upgraded to grub 2 and updated the kernal list and everything worked fine as far as sound goes.

I dont remember the link but try upgrading to grub 2 theres plenty of tutorials out there

In my case it was a fresh install not an update

---

### Post by Fritzendugan on 2009-11-17
*bump*

still having the issue....

---

### Post by Yellow Pasque on 2009-11-18
ALSA is pre-installed, but it may help to build the latest version from source. THis script does it for you: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by Fritzendugan on 2009-11-21
see *edit*

---

