---
title: "ASUS EEE PC 900, ALC662 Module Loaded, ALSA setup but sound not working"
date: 2008-05-03
forum: Multimedia Software
---

### Post by RichLouth on 2008-05-03
Hello,

I'm trying to get the sound working on my ASUS EEE PC 900.

I installed Ubuntu 7.10 on it using the kernel from:
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/)
, to boot from a usb pen drive.

I got wireless working by following the instructions here:
[https://help.ubuntu.com/community/EeePC#head-bd037cc8ecf56215a6c6b4ea5de4ec32ef23fba1](https://help.ubuntu.com/community/EeePC#head-bd037cc8ecf56215a6c6b4ea5de4ec32ef23fba1)

Other than the sound not working everything else is just perfect:)

So I checked my ALSA settings and everything is unmuted and the volume is up.

Looking at:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
, I was able to find out with "cat /proc/asound/card0/codec#* | grep Codec" that my device is:
```
Codec: Realtek ALC662 rev1
```
and from "lspci -v":
```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6
Family) High Definition Audio Controller (rev 04)
       Subsystem: ASUSTeK Computer Inc. Unknown device 8337
       Flags: bus master, fast devsel, latency 0, IRQ 16
       Memory at f7eb8000 (64-bit, non-prefetchable) [size=16K]
       Capabilities: <access denied>
```
, that the eee pc 900 has a HDA Intel device.

So looking here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
, I figured out I needed to download and compile the latest drivers from alsa. But using the method there seemed to break the audio so coming back to:
[https://help.ubuntu.com/community/SoundTroubleshooting#head-083f68c150e8cc9de635a7ab89b8ccfc6100ecf8](https://help.ubuntu.com/community/SoundTroubleshooting#head-083f68c150e8cc9de635a7ab89b8ccfc6100ecf8)
, I followed these instructions and using "aplay -l":
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
```
, I can see that the module is correctly loaded.

I also went through every option available for ALC662 found in "ALSA-Configuration.txt" to add to "/etc/modprobe.d/alsa-base":
```
options snd-hda-intel model=3stack-dig
```
```
options snd-hda-intel model=3stack-6ch
```
```
options snd-hda-intel model=3stack-6ch-dig
```
```
options snd-hda-intel model=6stack-dig
```
```
options snd-hda-intel model=lenovo-101e
```
```
options snd-hda-intel model=eeepc-p701
```
```
options snd-hda-intel model=eeepc-ep20
```
, resetting between each one and checking the ALSA settings for muting and volume, plugging in headphones and without head phones:) But none of them worked:(

I can't think what else to do. I looked at:
[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)
, but further playing about broke the sound again. I've got the module loaded again and "aplay -l" shows that it is correctly loaded.

I just wondered if anyone had any ideas of what I can try next? I suspect that it's some quirk of the asus eee pc 900 that alsa doesn't support yet. After all there isn't a model=eeepc-p900 option. I might try the bleeding edge source next but I wanted to check if anyone knew of something I could try before that.

Thanks

---

### Post by Zorael on 2008-05-03
Have you tried model=asus?

Also, make sure you don't have any channels muted in alsamixer, of course. :>

---

### Post by Zorael on 2008-05-03
This should help.

> Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
  ATI SB450, SB600, RS600,
  VIA VT8251/VT8237A,
  SIS966, ULI M5461

    model - force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size)
    single_cmd  - Use single immediate commands to communicate with
  codecs (for debugging only)
    enable_msi - Enable Message Signaled Interrupt (MSI) (default = off)

    This module supports one card and autoprobe.

    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

   Model name Description
   ----------    -----------
 ALC880
   3stack 3-jack in back and a headphone out
   3stack-digout 3-jack in back, a HP out and a SPDIF out
   5stack 5-jack in back, 2-jack in front
   5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
   6stack 6-jack in back, 2-jack in front
   6stack-digout 6-jack with a SPDIF out
   w810  3-jack
   z71v  3-jack (HP shared SPDIF)
   asus  3-jack (ASUS Mobo)
   asus-w1v ASUS W1V
   asus-dig ASUS with SPDIF out
   asus-dig2 ASUS with SPDIF out (using GPIO2)
   uniwill 3-jack
   fujitsu Fujitsu Laptops (Pi1536)
   F1734  2-jack
   lg  LG laptop (m1 express dual)
   lg-lw  LG LW20/LW25 laptop
   tcl  TCL S700
   clevo  Clevo laptops (m520G, m665n)
   test  for testing/debugging purpose, almost all controls can be adjusted.  Appearing only when compiled with $CONFIG_SND_DEBUG=y
   auto  auto-config reading BIOS (default)

 ALC260
   hp  HP machines
   hp-3013 HP machines (3013-variant)
   fujitsu Fujitsu S7020
   acer  Acer TravelMate
   basic  fixed pin assignment (old default model)
   auto  auto-config reading BIOS (default)

 ALC262
   fujitsu Fujitsu Laptop
   hp-bpc HP xw4400/6400/8400/9400 laptops
   hp-bpc-d7000 HP BPC D7000
   benq  Benq ED8
   hippo  Hippo (ATI) with jack detection, Sony UX-90s
   hippo_1 Hippo (Benq) with jack detection
   basic  fixed pin assignment w/o SPDIF
   auto  auto-config reading BIOS (default)

 ALC882/885
   3stack-dig 3-jack with SPDIF I/O
   6stack-dig 6-jack digital with SPDIF I/O
   arima  Arima W820Di1
   macpro MacPro support
   auto  auto-config reading BIOS (default)

 ALC883/888
   3stack-dig 3-jack with SPDIF I/O
   6stack-dig 6-jack digital with SPDIF I/O
   3stack-6ch    3-jack 6-channel
   3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
   6stack-dig-demo  6-jack digital for Intel demo board
   acer  Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
   medion Medion Laptops
   targa-dig Targa/MSI
   targa-2ch-dig Targs/MSI with 2-channel
   laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
   auto  auto-config reading BIOS (default)

 ALC861/660
   3stack 3-jack
   3stack-dig 3-jack with SPDIF I/O
   6stack-dig 6-jack with SPDIF I/O
   3stack-660 3-jack (for ALC660)
   uniwill-m31 Uniwill M31 laptop
   toshiba Toshiba laptop support
   asus  Asus laptop support
   asus-laptop ASUS F2/F3 laptops
   auto  auto-config reading BIOS (default)

 ALC861VD/660VD
   3stack 3-jack
   3stack-dig 3-jack with SPDIF OUT
   6stack-dig 6-jack with SPDIF OUT
   3stack-660 3-jack (for ALC660VD)
   auto  auto-config reading BIOS (default)

 CMI9880
   minimal 3-jack in back
   min_fp 3-jack in back, 2-jack in front
   full  6-jack in back, 2-jack in front
   full_dig 6-jack in back, 2-jack in front, SPDIF I/O
   allout 5-jack in back, 2-jack in front, SPDIF out
   auto  auto-config reading BIOS (default)

 AD1981
   basic  3-jack (default)
   hp  HP nx6320
   thinkpad Lenovo Thinkpad T60/X60/Z60

 AD1986A
   6stack 6-jack, separate surrounds (default)
   3stack 3-stack, shared surrounds
   laptop 2-channel only (FSC V2060, Samsung M50)
   laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
   ultra  2-channel with EAPD (Samsung Ultra tablet PC)

 AD1988
   6stack 6-jack
   6stack-dig ditto with SPDIF
   3stack 3-jack
   3stack-dig ditto with SPDIF
   laptop 3-jack with hp-jack automute
   laptop-dig ditto with SPDIF
   auto  auto-config reading BIOS (default)
 
 Conexant 5045
   laptop Laptop config 
   test  for testing/debugging purpose, almost all controls can be adjusted.  Appearing only when compiled with $CONFIG_SND_DEBUG=y

 Conexant 5047
   laptop Basic Laptop config 
   laptop-hp Laptop config for some HP models (subdevice 30A5)
   laptop-eapd Laptop config with EAPD support
   test  for testing/debugging purpose, almost all controls can be adjusted.  Appearing only when compiled with $CONFIG_SND_DEBUG=y

 STAC9200/9205/9254
   ref  Reference board

 STAC9220/9221
   ref  Reference board
   3stack D945 3stack
   5stack D945 5stack + SPDIF
   macmini Intel Mac Mini
   macbook Intel Mac Book
   macbook-pro Intel Mac Book Pro

 STAC9202/9250/9251
   ref  Reference board, base config
   m2-2  Some Gateway MX series laptops
   m6  Some Gateway NX series laptops

 STAC9227/9228/9229/927x
   ref  Reference board
   3stack D965 3stack
   5stack D965 5stack + SPDIF

 STAC9872
   vaio  Setup for VAIO FE550G/SZ110
   vaio-ar Setup for VAIO AR

    If the default configuration doesn't work and one of the above
    matches with your device, report it together with the PCI
    subsystem ID (output of "lspci -nv") to ALSA BTS or alsa-devel
    ML (see the section "Links and Addresses").

    Note 2: If you get click noises on output, try the module option
     position_fix=1 or 2.  position_fix=1 will use the SD_LPIB
     register value without FIFO size correction as the current
     DMA pointer.  position_fix=2 will make the driver to use
     the position buffer instead of reading SD_LPIB register.
     (Usually SD_LPLIB register is more accurate than the
     position buffer.)

    NB: If you get many "azx_get_response timeout" messages at
    loading, it's likely a problem of interrupts (e.g. ACPI irq
    routing).  Try to boot with options like "pci=noacpi".  Also, you
    can try "single_cmd=1" module option.  This will switch the
    communication method between HDA controller and codecs to the
    single immediate commands instead of CORB/RIRB.  Basically, the
    single command mode is provided only for BIOS, and you won't get
    unsolicited events, too.  But, at least, this works independently
    from the irq.  Remember this is a last resort, and should be
    avoided as much as possible...
    
    The power-management is supported.

---

### Post by MattBD on 2008-05-03
Have you tried this?

[http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/)

---

### Post by RichLouth on 2008-05-03
Cheers Zorael,

I've checked alsamixer so many times it's been burnt onto the back of my retina:)

Trying "model=asus" and "model=3stack-660" didn't work:(
"position_fix=1" and "position_fix=2" didn't work:(
Boot option "pci=noacpi" didn't work:(
And the "last resort" of using "single_cmd=1" didn't work either:(

I suspect it's a problem with the module.

One thing I forgot to mention before was that in System -> Preferences -> Sound. I (obviously) can't hear any sound from the test buttons but the test button for "Sound capture" gives the following error:
```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert !
audioresample ! gconfaudiosink profile=chat'
```

I don't know if that means anything to anyone?

I know the sound works because it was working in the Xandros distro that came preinstalled. Although I noticed it wasn't using ALSA. 

Thanks for the link MattBD:) But that's for the ASUS EEE PC 701, which I think uses a different sound chipset...

---

### Post by Zorael on 2008-05-10
You could try again with compiling source files for the [FONT="Courier New"]snd_hda_intel[/FONT] module, with newer/older builds; I'm out of ideas. The model= trick worked awesome for me.

And, of course, after making the changes to that alsa-base file you'd need to restart alsa for changes to take effect, unless this was already mentioned.
```
$ sudo /etc/init.d/alsa-utils restart
```

---

### Post by limiter on 2008-05-16
I am having the same problem using Xubuntu.  I really don't want to go back to the factory Linux install (because i'd need to buy a bigger flash drive to install it from).  Any extra help on this issue would be fantastic

---

### Post by zdude on 2008-05-17
I had a problem with my sound card hda_intel and I install the backports-modules-generics and my sound worked. I doesn't hurt to try!

---

### Post by limiter on 2008-05-17
I have a related problem that may help us track down the issue.  Whenever I try to run one of the gnome games (i.e. Gnometris) it will suddenly quit if sound is enabled.  The terminal output is as follows:
```

(gnometris:5287): GStreamer-CRITICAL **" gst_element_get_bus: assertion 'GST_IS_ELEMENT (element)' failed

(gnometris:5287): GLib-GObject-CRITICAL **" g_object_set: assertion 'G_IS_OBJECT (element)' failed

(gnometris:5287): GStreamer-CRITICAL **" gst_element_set_state: assertion 'GST_IS_ELEMENT (element)' failed

(gnometris:5287): GStreamer-CRITICAL **" gst_bus_timed_pop: assertion 'GST_IS_BUS (bus)' failed

Segmentation fault

```

I couldn't copy this directly so if there is a type know that that is not the issue, thats just me.

So from this it appears that there is a problem with my gstreamer.  Could this help us figure out the issue with the rest of the sound not working?

---

