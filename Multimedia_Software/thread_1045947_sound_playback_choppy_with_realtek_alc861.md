---
title: "sound playback choppy with realtek alc861"
date: 2009-01-21
forum: Multimedia Software
---

### Post by ksheyman on 2009-01-21
Okay, I am very new to linux and I am having a problem. All sounds play extremely choppy and slow. I'm puzzled because it was doing this when i first installed the OS and then it stopped, and now it's doing it again. I've tried countless settings in sound preferences and I've restarted bunches of times. Any ideas? Please!!

Using Ubuntu 8.10
Realtek ALC861 soundcard
Toshiba a105-2061 laptop

---

### Post by svasilis on 2009-02-20
hi! Please Help! I have the same problem!

I installed 8.10 on a Toshiba Equim and the sound is distorted(choppy). I searched around, tried a few things, but with no success.
Here is some information I got by typing some commands in the terminal window:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

So it finds the sound card, installs it, but sound does not come out properly when playing games or trying to listen to music or even when I test the sound card through the 'Sound' dialogue (System>Preferences>Sound).
Se P.S. of this post for detailed laptop configuration.

Please help!
Thank you very much!

Vasilis


P.S. The laptop I have is a Toshiba Equium A100-549
Processor

Processor: Intel Celeron M 360 / 1.4 GHz

Data Bus Speed: 400 MHz

Chipset Type: ATI Radeon Xpress 200M
Cache memory

Type: L2 Cache

Installed Size: 1 MB
Ram

Installed Size: 1 GB / 2 GB (max)

Technology: DDR II SDRAM - 533 MHz

Configuration Features: 2 x 512 MB
Storage controller

Type: Serial ATA

Serial ATA Interface: Serial ATA-150
Storage

Hard Drive: 40 GB - Serial ATA-150 - 5400 rpm
Optical storage

Type: DVD±RW (±R DL) / DVD-RAM - integrated

Read Speed: 24x (CD) / 8x (DVD)

Write Speed: 24x (CD) / 8x (DVD±R) / 4x (DVD-R DL) / 2.4x (DVD+R DL)

CD / DVD Rewrite Speed: 16x (CD) / 6x (DVD-RW) / 8x (DVD+RW) / 5x (DVD-RAM)
Display

Display Type: 15.4" TFT

Max Resolution: 1280 x 800 ( WXGA )

Widescreen Display: Yes

Colour support: 24-bit (16.7 million colours)

Features: TruBrite
Video

Graphics Processor / Vendor: ATI Radeon Xpress 200M

Video Memory: Shared Video Memory (UMA)

Max Allocated RAM Size: 128 MB
Audio

Audio Output: Sound card

Audio Codec: Realtek ALC861

Compliant Standards: DirectSound, DirectSound3D, DirectMusic
Input device(s)
Type: Keyboard, touchpad

Modem: Fax / Modem

Max Transfer Rate: 56 Kbps

Protocols & Specifications: ITU V.34, ITU V.90

Features: Wake on Ring, V.92 upgradable
Networking

Networking: Network adapter

Wireless LAN Supported: Yes

Data Link Protocol: Ethernet, Fast Ethernet, IEEE 802.11b, IEEE 802.11g

Compliant Standards: IEEE 802.11b, IEEE 802.11g, Wi-Fi CERTIFIED

---

