---
title: "No Sound: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]"
date: 2011-06-16
forum: Multimedia Software
---

### Post by liamvhogan on 2011-06-16
I've a new (to me) HP DC7800 with an otherwise perfectly functional Ubuntu 11.04 installation, except that I have no sound, from anywhere, at all.

I'm quite certain I've unmuted everything possible, and I've been reading[ this very helpful sticky thread]("http://ubuntuforums.org/showthread.php?t=205449").

The contents of aplay -L are:

```
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions

```And I see this sound card in lspci -v (and in the Hardware tab of Sound Preferences):

```
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
    Subsystem: XFX Pine Group Inc. Device aa68
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f0020000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```Which is well and good, but when I try to plug a set of headphones into the headphone jack---or indeed any of the sound outputs I have---there is no sound.

This is my alsamixer display:

```
&#9474; Card: HD-Audio Generic                               F1:  Help               &#9474;
&#9474; Chip: ATI R6xx HDMI                                  F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF                                         Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                     &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                                     &#9474;OO&#9474;                                     &#9474;
&#9474;                                     &#9492;&#9472;&#9472;&#9496;                                     &#9474;
&#9474;                                  < S/PDIF >                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              
```I'd really appreciate any possible help or suggestions. Is my card supported by alsa, or by ubuntu? I can't immediately tell.

---

### Post by lidex on 2011-06-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by dcstar on 2011-06-19
> **liamvhogan said:**
> I've a new (to me) HP DC7800 with an otherwise perfectly functional Ubuntu 11.04 installation, except that I have no sound, from anywhere, at all.
........

Check in your BIOS if there is an option to use HDMI video somewhere, my ATI HDMI **audio** would not work until this was selected!

---

### Post by Yellow Pasque on 2011-06-19
Unfortunately, you need to use fglrx/Catalyst for HDMI audio on RadeonHD 5k/6k cards, so if you're using the open-source driver, that's the issue.

---

### Post by manty@debian.org on 2011-08-03
At least on current Debian Wheezy (still under development) radeon free driver (version 6.14.2) for xorg server version 7.6 this is working ok.  I'm testing this on a ATI Technologies Inc RV710 [Radeon HD 4350] and the audio device identifies itself as ATI Technologies Inc RV710/730 (ATI R6xx HDMI).  I'm currently running current wheezy's kernel 2.6.39.  The only thing I had to do so that apps would use the right device was to set /etc/asound.conf like this:  pcm.!default { type hw card 0 device 3 }  One weird thing I noticed was that I would loose the sound if I had something specified on a Monitor section for the HDMI-0 output, so my current xorg.conf is like this:
Section "Monitor"
     Identifier      "VGA-0"
     Modeline "1920x1080"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
     Option "PreferredMode" "1920x1080"
     Option "Primary" "false"
EndSection
Section "Screen"
    Identifier    "Default Screen"
    SubSection "Display"
        Depth           24
        Modes        "1920x1080"
    EndSubSection
EndSection

---

### Post by T.E.N. on 2011-10-30
> **liamvhogan said:**
> I've a new (to me) HP DC7800 with an otherwise perfectly functional Ubuntu 11.04 installation, except that I have no sound, from anywhere, at all.
[...]
I'd really appreciate any possible help or suggestions. Is my card supported by alsa, or by ubuntu? I can't immediately tell.

As per [http://h30499.www3.hp.com/t5/Business-PCs-Deskpro-EVO/DC7800-CMT-Digital-audio-output-and-other-pinouts/m-p/5363241#M84600](http://h30499.www3.hp.com/t5/Business-PCs-Deskpro-EVO/DC7800-CMT-Digital-audio-output-and-other-pinouts/m-p/5363241#M84600) and further references therein (as well as spec sheets in places such as [http://www.epinions.com/specs/Hewlett_Packard_HP_dc7800_SFF_Core_2_Duo_E6750_2_66GHz_4MBL2_1333MHz_2GB_160GB_DVD_RW_GigNIC_VB_w_vPro_GQ650AW_ABA_PC](http://www.epinions.com/specs/Hewlett_Packard_HP_dc7800_SFF_Core_2_Duo_E6750_2_66GHz_4MBL2_1333MHz_2GB_160GB_DVD_RW_GigNIC_VB_w_vPro_GQ650AW_ABA_PC)), the on-board AD1884 should also have S/P-DIF, even capable of PCM/AC3 (5.1) output.

However, it is not known where this output ends up - neither an LED in a 3.5mm socket nor a pin header to connect it (or a coaxial S/P-DIF) has been identified so far, and the datasheet makes no mention what the external circuitry (if any) in addition to e.g. a TOTX195 should be.

Also, there seems to be a related thread concerning SuSE at [http://linux.bigresource.com/OpenSUSE-Hardware-HP-DC7800-No-sound-from-Speakers-Headphone-working-fine--AB65fTafg.html](http://linux.bigresource.com/OpenSUSE-Hardware-HP-DC7800-No-sound-from-Speakers-Headphone-working-fine--AB65fTafg.html)

Moreover, the HP DC7800's "Grizzly" mainboard does not seem to support more than one floppy disk drive - or does yours recognize /dev/fd1 ?

---

