---
title: "Sound drivers removed and sound card disabled, help pls."
date: 2009-10-22
forum: Multimedia Software
---

### Post by GabboCZ on 2009-10-22
Hi, 
I've got really stuck with this stupid problem. I had shitty and noisy sound in headphones on my F-S Amilo Pi1556 laptop. It has Realtek 880 onboard soundcard, so I decided to instal original drivers from realtek site. I launched install script, it deleted old drivers and than were some errors . So now I have no sound and I cant install that realtek driver. Can someone help me pls?

**Here are some info:**

```
#alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
```


alsa-base is installed. For grins I reinstalled but no good.

More information: When I run sound properties (gnome-sound-properties) it gives me the following error:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

```

lshw gives
```
#lshw
        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
```


Here are some interesting things. First, there is no sound adapter listed for "Default mixer tracks" in the sound configuration. 
I Also tried forcing alsa to reload and got the following errors.

```
#sudo alsa force-reload

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim/.gvfs
Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim/.gvfs
Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
```

here is output of lspci
```
#sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b1000000-b2ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: [88] Subsystem: Fujitsu Siemens Computers Device 10b0
	Capabilities: [80] Power Management version 2
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [140] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	Memory behind bridge: fac00000-febfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Fujitsu Siemens Computers Device 10b0
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: b3000000-b30fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Fujitsu Siemens Computers Device 10b0
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at b0004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: b3100000-b31fffff
	Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
	Capabilities: [50] Subsystem: Fujitsu Siemens Computers Device 10b0

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1880 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2300
	I/O ports at 18c8 [size=8]
	I/O ports at 18ac [size=4]
	I/O ports at 18c0 [size=8]
	I/O ports at 18a8 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at b0004400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at 2000 [size=128]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	Memory at b3000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 6b-76-2a-ff-ff-de-18-00
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at b3104000 (32-bit, non-prefetchable) [size=2K]
	Memory at b3100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
	Subsystem: Fujitsu Siemens Computers Device 10b0
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at 3000 [size=256]
	Memory at b3104800 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: r8169
	Kernel modules: r8169


```

```
#aplay -l
aplay: device_list:217: no soundcards found...
```

Thans for your help.

---

### Post by Ulysses361 on 2009-10-23
Hi,

Please execute step 1, reboot and then send us output from step 3 and step 4 from the following procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Regards,

Mark Rijckenberg

---

### Post by RichardLinx on 2009-10-23
Open a terminal and type:
```
sudo apt-get remove --purge pulseaudio
```
```
rm ~/.pulse-cookie
```

```
mv ~/.pulse ~/.pulse.backup
```


```
sudo apt-get install esound
```

```
sudo apt-get remove gstreamer0.10-pulseaudio
```

```
sudo apt-get install gstreamer0.10-esd
```

```
sudo /etc/init.d/alsa-utils restart
```

Reboot, sound should be working fine.

---

