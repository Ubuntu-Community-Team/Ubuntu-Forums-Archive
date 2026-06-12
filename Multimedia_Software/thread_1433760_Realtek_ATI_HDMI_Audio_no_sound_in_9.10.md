---
title: "Realtek ATI HDMI Audio no sound in 9.10"
date: 2010-03-19
forum: Multimedia Software
---

### Post by Steve'O on 2010-03-19
Hi all, newbie here. I was running Ubuntu 9.04 and just upgraded to 9.10 recently. I see many others are having problems with their sound. I too do not have sound. I did get sound running briefly with an Alsa update, but it was muffled. In trying many other fixes, I again have no sound and can not resolve it. I am thinking of burning a new cd and doing a fresh install and starting over.

My lap top is an MSI GT725 US model with an HD4850 mobility graphics card. I dual boot between Vista 32 bit and Ubuntu.

Has anyone else had any luck getting the Realtek ATI sound working in 9.10?:confused:

---

### Post by kazakore on 2010-03-19
I've had little problems getting some sound but getting everything working together is another matter.

This is my first Linux install, Ubuntu Studio 9.10, and want it for music and graphics/video so more on a slightly professional side than your average user (although only using onboard sound 90% of the time at the moment.)

Initial discovery was that it was loads noisier than on WinXP and it distorted very bad at a much lower level. First thing seemed to be make sure everything was good in the ALSA Mixer. (Saying that at first any single thing turned down seemed to mute output and not sure what cured it.) There is something strange than some seem to use the Surround output, which others use Front. Surely everything should come out my main, Front stereo pair as I'm only using a stereo output and have nothing set to multi-channel sound as far as I know.

And I have definitely slightly broken some part of PulseAudio as I can't restart it after cancelling it to get Jack to work for professional use but if you just want general audio using PA and ALSA the good news is it should be quite possible. Although I think people have got in deeper problems from upgrades than fresh installs from my limited reading.

---

### Post by Steve'O on 2010-03-19
Anyone else with Realtek sound issues have any resolutions?

---

### Post by Yellow Pasque on 2010-03-19
There are lots of Realtek codecs. Can you post the output of:
```
aplay -l
```
Also, did you run the ALSA upgrade script, or are you referring to some other ALSA update?

---

### Post by fabioa1978 on 2010-12-05
Hello All,
ion of 
I have a sony vaio VPCEB13FX. Im newbie to Linux and its my first installation. The sound is not working. I was looking for the driver for the sound card. I saw on the sony website that the card is onboard and its called REALTEK HDMI Audio driver. I cannot find the driver in order to make the sound work. Ubuntu find the Sound card and detects it. I tried to load the O/S so many times and still not working.

I ran the command aplay -l and gives me the following information:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

then I tried the command  lspci -v :

fabioa@fabioa-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 35
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e080 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f600a000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f6008000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f4c00000-f5ffffff
    Prefetchable memory behind bridge: 00000000f6100000-00000000f62fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f3800000-f4bfffff
    Prefetchable memory behind bridge: 00000000f6300000-00000000f64fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f2400000-f37fffff
    Prefetchable memory behind bridge: 00000000f6500000-00000000f66fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f0400000-f23fffff
    Prefetchable memory behind bridge: 00000000f6700000-00000000f68fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f6007000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 33
    I/O ports at e070 [size=8]
    I/O ports at e060 [size=4]
    I/O ports at e050 [size=8]
    I/O ports at e040 [size=4]
    I/O ports at e020 [size=32]
    Memory at f6006000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Sony Corporation Device 9071
    Flags: medium devsel, IRQ 4
    Memory at f6005000 (64-bit, non-prefetchable) [size=256]
    I/O ports at e000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 4
    Memory at f6004000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Foxconn International, Inc. Device e017
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f4c00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

03:00.0 SD Host controller: Ricoh Co Ltd Device e822
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f3802000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

03:00.1 System peripheral: Ricoh Co Ltd Device e230
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 4
    Memory at f3801000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

03:00.4 SD Host controller: Ricoh Co Ltd Device e822
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f3800000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 34
    Memory at f2420000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at b000 [size=256]
    Expansion ROM at f2400000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0
 

and then I went to the ASLA driver to see if i could find a driver for this sound card and I could not find it. 
Does anyone can help me with this???
I am enjoying it Ubuntu and I do not want to return to Win7.

Can you please give me some light where to find the drivers and how to execute the commands in order to make work?

Thanks

---

### Post by Yellow Pasque on 2010-12-06
^Are you trying to use the HDMI or the analog output?

---

### Post by lidex on 2010-12-25
Not sure of the alsa version coming in karmic, but if you want hdmi output I'm pretty sure you'll need 1.0.23. Check the output of this command:
```
cat /proc/asound/version
```
If you need to upgrade, follow the link in my sig.

---

