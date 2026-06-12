---
title: "[SOLVED] Shouldn't a Sound Blaster 16 PCI work?"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by LinuxNewb_22 on 2007-10-04
I just bought a new desktop and installed Ubuntu 7.04.

I was having sound problems with my motherboard (M2N-E SLI) - couldn't figure out how to get that going at all, and I did try everything. Then I decided to buy a cheap, older sound card that I thought would work - Creative Sound Blaster 16 PCI.

I've tried everything that I've read and nothing's working.

I went through the Comprehensive Sound Guide:
aplay -l detects my card, so does lspci (although it shows up as Creative Labs Ectiva EV1938). I went on alsa-project and downloaded, configured, compiled, and installed the appropriate alsa driver (which, according the the sound card matrix, is ens1371)... and STILL nothing.

I originally decided to go with an AMD processor and Linux OS because I thought it would end up being cheaper for a quick and powerful system than running and Intel processor and Windows OS. I've managed to get everything running except for sound. I'm really loving it, but just don't want to spend too much more money on the thing.

If anybody has an answer to or advice for this problem, I would really appreciate your help.

I love the system, it works beautifully, Ubuntu is amazing and looks fantastic with Compiz Fusion... 

...if only I could get the sound working.

---

### Post by LinuxNewb_22 on 2007-10-04
Ok, I'm hoping if I post my information someone will help me.

**$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**$ lspci -v**
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at fc00 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at dc00 [size=16]
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at c800 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=128
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fdf00000-fdffffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 812a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at c400 [size=8]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

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

01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at bc00 [size=128]
        Capabilities: <access denied>

01:06.0 Multimedia audio controller: Creative Labs Ectiva EV1938
        Subsystem: Creative Labs Unknown device 5938
        Flags: bus master, slow devsel, latency 32, IRQ 21
        I/O ports at b800 [size=64]
        I/O ports at b400 [size=32]
        Capabilities: <access denied>

05:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600] (prog-if 00 [VGA])
        Subsystem: PC Partner Limited Unknown device 0880
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fdef0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at ac00 [size=256]
        Expansion ROM at fdec0000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.1 Display controller: ATI Technologies Inc Unknown device 71e6
        Subsystem: PC Partner Limited Unknown device 0881
        Flags: fast devsel
        Memory at fdee0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

**$ sudo gedit /etc/modules**
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
snd-ens1371


**$ cat /proc/asound/modules**
 0 snd_ens1371

**$ sudo gedit /etc/modprobe.d/alsa-base**
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

As I wrote in the first post, I followed the Comprehensive Sound Problems Solution Guide, as well as the instructions from Alsa Project.

I got nothing for sound. I've tried to play an mp3 - when my mouse hovers over a song, a little musical note thing pops up (I know something's supposed to be playing at this point, but it's not). I double click that file and it opens up in MPlayer just fine. But I still hear nothing.

I've turned up all of the volumes in the volume control (for some reason I have 13 tracks in Playback - Master, Master Mono, Bass, Treble, PCM, Center, Line-in, CD, Microphone, Video, Phone, PC Speaker, Aux)... they're all at full volume, and so are my speakers.

When I go to System>Preferences>Sound (I don't have a "Multimedia controller" option), I can press "Test" on everything and there's no sound. There's no error where there used to be if I switched from AutoDetect to anything else, nor does it just close anymore when I press Test on Autodetect... but, no SOUND.

I would have thought that an older and basic card such as this would be no problem to set up.

I've noticed that a few people are having the same problem. Please, somebody help us if you can. I really have tried to exhaust all possibilities.

Thank you.

---

### Post by LinuxNewb_22 on 2007-10-04
I apologise for the very lengthy post, above. However, I was just trying to put up all information that I thought might be useful to someone knowledgeable.

---

### Post by LinuxNewb_22 on 2007-10-15
Someone please help me. I even did a fresh install, followed the Comprehensive Sound Problems Solutions Guide and updated from fresh kernel as well as alsa AGAIN... and still nothing.

I went out and bought the Sound Blaster 16 PCI because my onboard sound wasn't working in the first place (ASUS M2N-E SLI -- registers as USB audio).

Please, anyone, what should I do?

---

### Post by serfcx on 2007-10-15
I have the same old card and it works fine.
I think you may have to look at your BIOS and see if there is an option to disable sound from your motherboard, maybe this is causing conflicts.

Good luck

---

### Post by LinuxNewb_22 on 2007-10-15
I disabled the onboard sound card in BIOS so the only thing that Feisty detected on the fresh install was the SB16 card... which, btw, comes out as Ensoniq ES1371...weird.

This is the only thing left for me to fix... got my ATI card going, Compiz... even a RAID 0 configuration... but no sound. yargh.

---

### Post by serfcx on 2007-10-16
OK, here are my outputs for the same card

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci -v
00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI128
        Flags: bus master, slow devsel, latency 32, IRQ 12
        I/O ports at d400 [size=64]
        Capabilities: [dc] Power Management version 1

So same hardware device but different controller.

Have you tried to see if you have sound when using a live CD ? Try downloading and burning a live CD such as PCLinuxOS and see if it detects and plays sound.

I did have to relocate my soundblaster into a different PCI slot as it was conflicting with another card supplying additional USB ports. I removed that card then installed Ubuntu which found the audio card OK and gave me sound and then plugged back in the USB PCI card later and now both work.

Also check that your audio lead from your CD or DVD drive is connected to your soundblaster card before you install Ubuntu.

Thats about as far as I can go with help at this time. Good luck !

---

### Post by wsmoser2004 on 2007-10-16
I think I responded to your post in another thread LinuxNewb_22, but here it is again.  Hopefully it's helpful, since I'm posting it twice :).

I might be able to help!  I have the Gateway Solo 2150 laptop with the EV1938, which I believe has the same chipset as your desktop card.  At a high level, basically what I had to do to get this working was to use OSS for my sound driver, instead of ALSA.  I have a lot of annoying problems with OSS (my volume control doesn't work, for example :)) but at least I have sound.  Your mileage may vary.

Basically here's what you'll want to do.  You want to "blacklist" the ALSA kernel module so that Ubuntu doesn't try to use ALSA.  To do that, open a terminal and type

```

sudo gedit /etc/modprobe.d/blacklist

```

At the end of the file, add

```

snd_ens1371

```

Now you will want to "un-blacklist" the OSS module.  To do that, 

```

sudo gedit /etc/modprobe.d/blacklist-oss

```

in the terminal, find the line that says "es1371", and put a # in front of it.  Then you'll have 

```

#es1371

```

on that line in the file.  Finally, you'll want to tell Ubuntu to load that module when you boot, so open up 

```

sudo gedit /etc/modules

```

and add 

```

es1371

``` 

to the end of the file.  Then, reboot.  You should now have sound!  Hopefully the volume control will work for you, it doesn't work for me in Xubuntu.  I just use the volume control in whatever application I happen to be using at the moment.

**EDIT: **I just noticed that you said you have snd-ens1371 in /etc/modules.  You'll want to take that out or add a # in front of it.  You DON'T want to use snd-ens1371, that's the ALSA driver which doesn't work for whatever reason.

I also don't know whether the desktop PCI card will work the same as the laptop card.  Let me know how it works!

---

### Post by jso2897 on 2007-10-17
I'm not sure you should have all those volume controls on. Try going into the volume control console, Edit>Preferences, and uncheck everything except  Master,PCI, Line-In, CD, Microphone and PC Speaker, and see if that helps.

---

### Post by LinuxNewb_22 on 2007-10-18
SOLVED!!

wsmoser2004.... Thank you, thank you, thank you... THANK YOU!!!!

---

### Post by LinuxNewb_22 on 2007-10-18
... now any idea how to get the sound working in Flash in Firefox to enjoy YouTube videos... ?

---

### Post by wsmoser2004 on 2007-10-19
LinuxNewb_22 -

Good to hear your sound is working!  I know that I have Flash sound working in Firefox on that laptop, but I am not using it right now.  As soon as I use it again I'll let you know how it's done.

I do remember having to goof around to get it to work though...that's one of those annoying nuances I mentioned before. ;-)

- wsmoser2004

---

### Post by wsmoser2004 on 2007-10-20
LinuxNewb_22 -

I found [this]("http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux") page that explains how to get sound working in Firefox.  You shouldn't need to do all of that, just follow my directions and you should be good.  I already compiled it for you and it's attached, so it should be relatively simple.

I had to gzip the file so I could attach it, so download that and then do

```

gunzip libflashsupport.so.gz

```

That should unzip to the file libflashsupport.so.  This next command supposedly is just to make sure that nothing is broken.  It shouldn't be, since I compiled it and it looks like it works.  But do it anyway :).  It'll spew a bunch of stuff, as long as you don't see any errors it's probably OK.  (Note: If you don't have the ldd command, just skip this step.  I'm not sure if it's part of a default install or not.)

```

ldd libflashsupport.so

```

Then you'll need to put libflashsupport.so in your /usr/lib, so do a 

```

sudo cp libflashsupport.so /usr/lib

```

Restart Firefox, and your sound should work!  Or at least it did for me on a (mostly) clean install.  Enjoy!

- wsmoser2004

---

### Post by LinuxNewb_22 on 2007-10-31
wsmoser2004! I JUST saw this reply even though I subscribe to the thread!

IT WORKED!

YOU, my friend, are a gentleman (I'm going with the presumption that you're one of the 99% of the geeks on here, including me, that is male) and a scholar. Hats off to you, fine sir!

Thank you, once again.

---

### Post by s@giv on 2007-12-25
hay i am relatively a new ubuntu user and i have a similar problem on my xubuntu os it has creative soundblaster 128 pci card and no sound can u help me?


$ aplay -l
aplay: device_list:204: no soundcards found...


$ lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 1.0

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fa600000-fe6fffff
        Prefetchable memory behind bridge: ee400000-f24fffff

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at ef80 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

00:0f.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 08)
        Subsystem: Intel Corporation EtherExpress PRO/100+ Management Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at febff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ef00 [size=64]
        Memory at fea00000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at fe900000 [disabled] [size=1M]
        Capabilities: [dc] Power Management version 2

00:12.0 Multimedia audio controller: Fishcamp Engineering Unknown device 1331
        !!! Invalid class 0401 for header type 01
        Flags: bus master, VGA palette snoop, fast Back2Back, 66MHz, user-definable features, medium devsel, latency 0
        [virtual] Memory at 20000000 (32-bit, non-prefetchable) [disabled] [size=128]
        I/O ports at 20000080 [disabled] [size=128]
        Bus: primary=00, secondary=00, subordinate=00, sec-latency=0
        !!! Unknown I/O range types 4/0
        Memory behind bridge: 00000000-000fffff
        !!! Unknown prefetchable memory range types 4/0
        Capabilities: [04] #34 [1371]
        Capabilities: [10] #00 [0000]

01:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01) (prog-if 00 [VGA])
        Subsystem: 3Dfx Interactive, Inc. Voodoo3 AGP
        Flags: 66MHz, fast devsel, IRQ 11
        Memory at fc000000 (32-bit, non-prefetchable) [size=32M]
        Memory at f0000000 (32-bit, prefetchable) [size=32M]
        I/O ports at d800 [size=256]
        Expansion ROM at fe6f0000 [disabled] [size=64K]
        Capabilities: [54] AGP version 1.0
        Capabilities: [60] Power Management version 1

$ sudo gedit /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

$ sudo gedit /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

