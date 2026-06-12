---
title: "No sound card detected after ATI graphics card driver installation"
date: 2009-03-23
forum: Multimedia Software
---

### Post by tai-pan on 2009-03-23
I'm still new to linux, so please bare with me.  I've searched for a solution to my problem, but it appears to be a unique one off of the many sound issues I come across.

I'm running 8.10, the 2.6.27-11-generic kernal. Sound was working fine until I installed the ATI proprietary graphics drivers, as per the manual install instructions found here:

[wiki.cchtml.com]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually")

Now there's a red x over my menu bar volume control and I get the following message when clicking on it:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

Also aplay -l gives me the following

apollo:~$ aplay -l
aplay: device_list:215: no soundcards found...

I've tried rolling back to previous kernals, but then my graphics driver poops out on me with a dead, black screen.  If anyone has any leads or insights, I'd be most appreciative.  I suspect it has something to do with the Access Denied line in the following truncated lspci output:

apollo:~$ lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, slow devsel, latency 32, IRQ 4
	Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

Here's a full lspci output:

apollo:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Giga-byte Technology Device 5000
	Flags: bus master, 66MHz, medium devsel, latency 32

00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
	I/O ports at ff00 [size=8]
	I/O ports at fe00 [size=4]
	I/O ports at fd00 [size=8]
	I/O ports at fc00 [size=4]
	I/O ports at fb00 [size=16]
	Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
	Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Giga-byte Technology Device 4385
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device 5002
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f900 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: ata_generic, pata_acpi, pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, slow devsel, latency 32, IRQ 4
	Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Giga-byte Technology Device 5001
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fdd00000-fddfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]
	Subsystem: Micro-Star International Co., Ltd. Device 1620
	Flags: bus master, fast devsel, latency 0, IRQ 2302
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdfe0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at ee00 [size=256]
	[virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:00.1 Audio device: ATI Technologies Inc RV730XT Audio device [Radeon HD 4670]
	Subsystem: Micro-Star International Co., Ltd. Device aa38
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at fdffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Giga-byte Technology Device 1000
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fdef8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
	I/O ports at de00 [size=256]
	Memory at fdefe000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

---

### Post by markbuntu on 2009-03-23
That driver adds another hardware sound device for HDMI so the first thing you should try is reinstalling ALSA so it can automagically reconfigure itself.


(1) Remove the ALSA packages. From a terminal (Applications/Accessories/Terminal):
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

You can also go here for more info/help about sound in Ubuntu/Linux

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by tai-pan on 2009-03-25
Thanks for the thought, but unfortunately this doesn't solve the problem. I actually tried the same thing prior to posting and again after you recommended it.  But upon reboot, I obtain the exact same symptoms I listed above.

Any other ideas? I'd really like my sound back.

Thanks for any help anyone can provide; I really am banging my head against the wall on this one.

---

### Post by tai-pan on 2009-03-25
Still trying to figure this out, I wonder if the cause of the problem is indeed the extra sound device. Here's a partial output of sudo lspci -v (all audio devices are listed below), which side steps the access denied comment I made in the first post (duh, sudo!):

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, slow devsel, latency 32, IRQ 4
	Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2

 01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
	Subsystem: Micro-Star International Co., Ltd. Device aa38
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at fdffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>

The first device is my motherboard's built in sound device.  This is the one I want.  The second is something that seems to have shown up after I installed the ATI drivers. My graphics card is a Micro-Star International brand.

So how do I tell ubuntu to detect the first and not the second?

---

### Post by tai-pan on 2009-03-25
Ok, more relevant info regarding the bug.

1) no /proc/asound/ directory on my machine
2) no system-config-sound on my machine
3) System > Preferences > Sound: Default Mixer Tracks Device drop down list is empty - despite lspci showing two audio devices, I can't select either of them
4) problems with alsamixer

apollo:~$ sudo alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

I guessing the ATI driver install did something to my alsa configuration, but as I mentioned before, doing a purge and clean reinstall of alsa does not fix the problem.

---

### Post by markbuntu on 2009-03-25
Did you reboot?
Sorry to ask that but sometimes people forget that they need to reboot.

The gpu on IRQ 2302 also looks a little suspicious. Have you looked in the bios to see if anything is disabled, etc?

---

### Post by tai-pan on 2009-03-27
Yes, I did reboot.  I also checked my BIOS settings, nothing looks disabled.  I dual boot Ubuntu with XP and XP interfaces with the sound card just fine, so I don't think anything regarding BIOS is the problem; this appears to be unique to Ubuntu.

Any other suggestions? Really, I appreciate them all and I'm willing to try anything at this point.

Many thanks.

---

### Post by tai-pan on 2009-03-27
Interesting development: I tried to disable the on board sound card though the BIOS to see if having only one detected device would fix my problem, but doing so resulted in the following lspci output:

apollo:~$  lspci | grep audio
apollo:~$ 

As you might guess, I have no sound still.  But it's curious to me that this killed the sound device that is detected on the graphics driver as well.

---

### Post by markbuntu on 2009-03-27
That is very weird. Do you have the latest bios for that mobo?

---

### Post by dspisak on 2009-03-27
Hi, tai-pan.  I have the same problem as you.  I installed a new MB with the old HD.  After boot ubuntu 8.10 found all the devices and their drivers except for the ATI drivers in System/Administration/Hardware Drivers.  After I installed those ATI drivers my monitor was able to run at native resolution (2048x1152) and I had reliable sound for several days.  However, I then loaded the Linux audio drivers from the MB manufacturer's setup disk.  Now aplay -l returns " device_list:215: no soundcards found...".  Since I am new to Linux I am at a loss as to how to remove the drivers.  I've tried many of the suggestions in the forums (ALSA in and out, pulseaudio in and out, etc.) but nothing works.  Of course, the sound works great when I boot to XP.  I would really appreciate some help.

Computer:
MB - Asus M3A78-T, 0802 bios
CPU - AMD Phenom II x4 810, 3.18 GHz
RAM - 2 GB Crucial PC8500
On-board Video - ATI Radeon HD 3300
On-board Audio - ATI RS780 Azalia (or ATI Technologies Inc SBx00 Azalia (Intel HDA)
 according to lspci -v)

Dan

Edit: The ATI driver loaded from Hardware Drivers is "ATI/AMD proprietary FGLRX graphics driver".  I deactivated then activated it.  The sound card was not found.

3/29 edit: I was using ubuntu 8.10, 2.6.27-11.  I rebooted to kernel 2.6.27-7 and the sound now works fine.  I noticed that the pci folder which contains the snd-hda-intel driver was not included in the -11 kernel files.  I copied the pci folder from the -7 folder to the -11 folder and rebooted.  Still no sound when running -11.  So, running kernel -7 has good sound.  However, I cannot load the ATI/AMD proprietary FGLRX graphics driver when runnig -7 so I am stuck in low resolution mode.

Question: Is it possible to re-install the -11 kernel without re-installing all of unbuntu 8.10?

Question: Is there an alternate way to install the ATI/AMD proprietary FGLRX graphics driver?  I've tried Synaptic without success.

TIA

4/6/09 edit: The problem is solved.  I followed soundcheck's instructions on the "ALSA Upgrade Script" thread and re-installed ALSA.  I did not have to re-install either ubuntu or the kernel.  The video was not affected.

Dan

---

