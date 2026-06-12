---
title: "Sound Card Selection"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by colsandurz on 2007-06-20
Hi, my PC has an integrated sound card and an Audigy 1.  The integrated sound card is selected always, no matter what card I select in Volume Control... why doesn't Ubuntu respond when I make this change and how can I fix this?

Here's my lspci
```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3)
02:01.0 USB Controller: NEC Corporation USB (rev 41)
02:01.1 USB Controller: NEC Corporation USB (rev 41)
02:01.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:0a.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
02:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
02:0b.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:0c.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

These are the two devices 

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 04)
02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
```

Thanks for any help....

---

### Post by marc321 on 2007-06-20
First, try this.  Go to System -> Preferences -> Sound.  In the drop-down boxes for sound playback, etc., choose your Audigy card and press the "Test" button.  Be prepared for an annoying high pitch sound.  If it works, close out of Sound Preferences.  That may work.

You may just have to disable onboard sound in the CMOS setup on your computer.  When you boot up your computer, it should tell you which key you have to press to enter the CMOS setup (usually F1, F2, F10 or Del).

Once in, use the arrow keys to find an area usually labeled "Integrated Peripherals."  In the list of peripherals, find onboard sound/audio, and, following the directions at the bottom of the screen, change it to disabled.  This is usually a matter of pressing enter and selecting an entry from a pop-up list, using the left or right arrow keys, or using Pg-Up/Pg-Down.

I am making the assumption here that you don't want to use the onboard sound at all, ever.

There is another option as well, if you prefer.  Run:

```

lsmod | grep snd

```

Look for something related to intel, like snd_intel8x0.  If you find it, do this:

```

sudo echo "snd_intelxxx" >> /etc/modprobe.d/blacklist

```

where snd_intelxxx is the module you found.  Reboot and it should be gone.

---

