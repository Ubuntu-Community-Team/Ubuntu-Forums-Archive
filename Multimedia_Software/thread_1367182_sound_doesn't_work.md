---
title: "sound doesn't work"
date: 2009-12-29
forum: Multimedia Software
---

### Post by haneczka on 2009-12-29
Hi, all

I'm turning to you after few days of fighting with the system. I have no more ideas and whatever I do, it doesn't work.

I started playing with sound a couple of days ago because my mic didn't work. During this time I have updated, upgraded, disabled and enabled, uninstalled and installed again. And now the sound doesn't work at all. Although sound controls show that  both speakers and mic work. Still, I can't hear a thing. Could you please help me fix it?

I'm running Karmic on my HP dv6. 

> $ aplay -l
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0> $ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d2300000-d23fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: d1300000-d22fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: d1200000-d12fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d2500000-d25fffff
    Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    Memory behind bridge: d1100000-d11fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 6038 [size=8]
    I/O ports at 604c [size=4]
    I/O ports at 6030 [size=8]
    I/O ports at 6048 [size=4]
    I/O ports at 6010 [size=16]
    Memory at d2408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at d2407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at d2406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d2408500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d2405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d2404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at d2408400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: 66MHz, medium devsel
    Capabilities: <access denied>
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 6000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
    I/O behind bridge: 00001000-00001fff

00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
    Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=256]
    Memory at d2300000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at d2320000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at d2310000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Hewlett-Packard Company Device 3040
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d1200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3060
    Flags: bus master, fast devsel, latency 0, IRQ 30
    I/O ports at 2000 [size=256]
    Memory at d1004000 (64-bit, prefetchable) [size=4K]
    Memory at d1000000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at d1010000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169> $ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Dec 27 2009 for kernel 2.6.31-16-generic (SMP).Oh, and please, I'm not that smart. Please tell me what to write in the command line, not what I should do ;)

Thanks, 
Hanna

---

### Post by VertexPusher on 2009-12-29
Open a terminal window and enter this:
```
speaker-test -t wav -c 2 -D plughw:0,0
```
This will play back test sounds on the left and right speaker. You can stop the test by pressing Ctrl-C.

If the test proceeds without an error message but you don't hear anything, check your mixer settings. Run alsamixer or gnome-alsamixer and turn all the sliders up until you hear something.

If the test program aborts with an error message, copy and paste it here.

---

### Post by haneczka on 2009-12-29
$ speaker-test -t wav -c 2 -D plughw:0,0

speaker-test 1.0.21

Playback device is plughw:0,0
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 2.731511
 0 - Front Left
 1 - Front Right
Time per period = 3.070089
 0 - Front Left
 1 - Front Right
Time per period = 2.899927
 0 - Front Left
 1 - Front Right

... however, I can still hear no sound.

---

### Post by VertexPusher on 2009-12-29
> **haneczka said:**
> ... however, I can still hear no sound.
Did you turn up all the volume sliders in the mixer? If you use gnome-alsamixer, some sliders may be hidden by default. You can make them appear by changing the preferences.

---

### Post by haneczka on 2009-12-29
> **VertexPusher said:**
> Did you turn up all the volume sliders in the mixer? If you use gnome-alsamixer, some sliders may be hidden by default. You can make them appear by changing the preferences.

I have done all that. All the volumes are at maximum, everything unmuted (well, apart from the pc beep but i don't think that this matters here). I did that in sound options, pavucontrol and alsamixer. Still no sound.

To me, it looks as if there was something muting the speakers but I can't reach it. The system starts with sounds muted, I don't know why. But even when I set all the volumes at max, and one would think it will work, it doesn't.

---

### Post by VertexPusher on 2009-12-29
There are two sound cards in your computer. The first one (card 0) has two output devices, analog and digital.

"plughw:0,0" means that the test is run on the first device of card 0. In your case that is "STAC92xx Analog".

Is that the correct card/device? For example, if you use the digital output jack, "plughw:0,1" would be correct. If you use the HDMI output, "plughw:1,0" would be correct.

Are you using headphones? Did you activate the headphone jack in alsamixer?

---

### Post by haneczka on 2009-12-29
That's the thing that confused me a bit. I'm using the built-in speakers, so I think the analog output is relevant here. I assumed the HDMI stands for the socket in the laptop but I've never used it. 

I tried connecting the headphones and trying if the sound would work that way, but it didn't. 

The alsamixergui shows: Master, Speaker, PCM, Front, Capture and Mux at max levels and Mic Jack Mode, IEC958, IEC958 Default PCM and IEC958 Playback Source at 0 and I can't move those controls.

---

### Post by VertexPusher on 2009-12-29
What did you install/uninstall when your microphone didn't work? Maybe it would help to reinstall all the base ALSA packages to get the system back to its original state.

---

### Post by haneczka on 2009-12-29
Ooohh... I didn't do much. I added pavucontrol and earcandy (that doesn't work). Apart from that I uninstalled PulseAudio at some point but as nothing worked then, I reinstalled it again.

Basically, I think most of the things are the same... If there is something else, I really don't know what. And, well, the sound is not working any more.

---

### Post by VertexPusher on 2009-12-29
Well, there must be something that triggered the change from "mic not working" to "sound not working".

Did you install Ubuntu from a live CD? What if you boot the live CD again and check if sound works there? The live CD is the easiest way to test these things on a "default" setup.

---

### Post by haneczka on 2009-12-29
I have no idea what is wrong. I don't even have a live CD.

---

### Post by haneczka on 2009-12-29
Good. I managed to get somewhere with this! 

1. I've found the linux-blackports-modules-alsa modules. Command line said it can't find the packages, synaptics found them. I got sound at login after reboot! 

2. I turned off the HDMI output! I can listen to the music now.

But the mic still doesn't work... Any ideas? I really appreciate help here.

---

### Post by VertexPusher on 2009-12-29
This command will capture audio from your sound card and play it back at the same time:
```
arecord -D plughw:0,0 -f S16_LE -r 48000 -c 2 | aplay -D plughw:0,0 -f S16_LE -r 48000 -c 2
```
Again, while it is running, use alsamixer to select the recording source and adjust the capture volume sliders until you hear the mic input signal.

Be careful not to move the mic too close to the speakers to avoid a feedback loop while testing.

---

### Post by haneczka on 2009-12-29
$ arecord -D plughw:0,0 -f S16_LE -r 48000 -c 2 | aplay -D plughw:0,0 -f s16_LE -r 48000 -c 2
Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
Playing WAVE 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
arecord: pcm_read:1617: read error: Input/output error

and it makes a short "DZZT" noise to it. 

Something wrong with the mic, then?

---

### Post by VertexPusher on 2009-12-29
> **haneczka said:**
> Something wrong with the mic, then?
No, this is a software-related problem. The arecord command should work even if there is no mic attached at all.

Input/output errors may occur when the device is busy, i.e. opened by another application, e.g. PulseAudio.

Try running the command like this:
```
pasuspender -- arecord -D plughw:0,0 -f S16_LE -r 48000 -c 2 | aplay -D plughw:0,0 -f S16_LE -r 48000 -c 2
```
pasuspender is a tool to temporarily suspend PulseAudio and release its audio devices so that they can be used by other programs.

---

### Post by haneczka on 2009-12-29
$ pasuspender -- arecord -D plughw:0,0 -f S16_LE -r 48000 -c 2 | aplay -D plughw:0,0 -f S16_LE -r 48000 -c 2
Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
Playing WAVE 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
arecord: pcm_read:1617: read error: Input/output error

---

