---
title: "Audiophile 2496 w/ ALSA 1.024 - $50 for the person who helps me with this"
date: 2011-03-16
forum: Multimedia Software
---

### Post by ranperry on 2011-03-16
Ubuntu 10.10 server 64bit
M-Audio Audiophile 2496

lsmod:

snd_ice1712            66696  0 
snd_ice17xx_ak4xxx      3115  1 snd_ice1712
snd_ak4xxx_adda         9318  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              7938  1 snd_ice1712
snd_ac97_codec        125227  1 snd_ice1712
snd_pcm                88118  2 snd_ice1712,snd_ac97_codec
snd_page_alloc          8588  1 snd_pcm
ac97_bus                1474  1 snd_ac97_codec
snd_i2c                 5574  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         6849  1 snd_ice1712
snd_seq_midi            5932  0 
snd_rawmidi            21775  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57032  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23518  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    63620  11 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd


aplay -l:

aplay: device_list:240: no soundcards found...

aplay -L:

null
    Discard all samples (playback) or generate zero samples (capture)

---

### Post by cchhrriiss121212 on 2011-03-17
Can you post lspci -v?

---

### Post by ranperry on 2011-03-17
```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
	Subsystem: Intel Corporation Device 574d
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Device 574d
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at e0200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 30c0 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at e0100000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: e0300000-e06fffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000e00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: e0700000-e08fffff
	Prefetchable memory behind bridge: 00000000e0900000-00000000e0afffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: e0b00000-e0cfffff
	Prefetchable memory behind bridge: 00000000e0d00000-00000000e0efffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: e0f00000-e10fffff
	Prefetchable memory behind bridge: 00000000e1100000-00000000e12fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Device 574d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 3080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Device 574d
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 3060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Device 574d
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 3040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Device 574d
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 3020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Device 574d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at e0280400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 01)
	Subsystem: Intel Corporation Device 574d
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Device 574d
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 30b8 [size=8]
	I/O ports at 30cc [size=4]
	I/O ports at 30b0 [size=8]
	I/O ports at 30c8 [size=4]
	I/O ports at 30a0 [size=16]
	Memory at e0280000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
	Subsystem: Intel Corporation Device 574d
	Flags: medium devsel, IRQ 10
	I/O ports at 3000 [size=32]
	Kernel modules: i2c-i801

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Intel Corporation Device d625
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at 2000 [size=256]
	Memory at e0004000 (64-bit, prefetchable) [size=4K]
	Memory at e0000000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

05:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
	Subsystem: VIA Technologies Inc. M-Audio Delta Audiophile 2496
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at 1040 [size=32]
	I/O ports at 1070 [size=16]
	I/O ports at 1060 [size=16]
	I/O ports at 1000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ICE1712
	Kernel modules: snd-ice1712

```

---

### Post by cchhrriiss121212 on 2011-03-17
The system sees the card, and the correct module is loaded, so the problem must be with ALSA. Have you made any modifications to ALSA since installing? eg upgraded to a newer version manually
Was there anything you did to fix the issue?

---

### Post by ranperry on 2011-03-17
I replaced the server installation with the desktop. Now everything looks ok as far as detecting the card:

aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


aplay -L:

```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    Front speakers
surround40:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    4.0 Surround output to Front and Rear speakers
surround41:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    Direct sample mixing device
dsnoop:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    Direct sample snooping device
hw:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    Direct hardware device without any conversions
plughw:CARD=M2496,DEV=0
    M Audio Audiophile 24/96, ICE1712 multi
    Hardware device with all software conversions

```


I want to use MPD but is crashes if I use the ALSA profile. My mpd.conf file:

```
audio_output {
        type            "alsa"
        name            "My ALSA Device"
        device          "plughw:0,0"    # optional
        format          "*:24_3:2"      # optional
#       mixer_type      "hardware"      # optional
#       mixer_device    "default"       # optional
#       mixer_control   "PCM"           # optional
#       mixer_index     "0"             # optional
}

```

mpd error log:

```
Mar 17 01:27 : mixer: Failed to read mixer for 'My ALSA Device': no such mixer control: PCM
Mar 17 07:32 : Failed to open mixer for 'My ALSA Device': no such mixer control: PCM

```

It works with Pulseaudio, but I need ALSA for bit perfect playback.

Thanks.

---

### Post by cchhrriiss121212 on 2011-03-17
I'm not an MPD user, but I think the crash is related to the multiple channels on the ICE1712 cards (it expects to have a single volume control instead of 12 separate ones). 

Try either or both of these fixes:
[http://www.linuxquestions.org/questions/ubuntu-63/no-sound-in-ubuntu-studio-with-m-audio-delta-44-a-781558/](http://www.linuxquestions.org/questions/ubuntu-63/no-sound-in-ubuntu-studio-with-m-audio-delta-44-a-781558/)
> [COLOR=Black]I've edited the /usr/share/alsa/cards/Ice1712.conf
like in this bugfix.
For this you have to open a terminal/konsole and you have to open
*gedit* as ROOT.

**> sudo gedit**
(after enter you have to type in your password!!!)

Than open [/COLOR]the folder:
**/usr/share/alsa/cards/**
find the file **Ice1712.conf** drag an drop it into *gedit*
find these entry like below and insert theses lines lines
(without the <---- add this):


ICE1712.pcm.front.0 {
        @args [ CARD ]
        @args.CARD {
                type string
        }
        type route
        ttable.0.0 1
        ttable.1.1 1
        slave.pcm {
                type hw
                card $CARD
        }
[B]        slave.format S32_LE            <---- add this
        slave.channels 10              <---- add this[/B]
}


After a restart I had the output of my Delta 44Or this:
[http://ubuntuforums.org/showpost.php?p=9317203&postcount=2](http://ubuntuforums.org/showpost.php?p=9317203&postcount=2)

---

### Post by samfuzz on 2011-03-17
for bit perfect try this  :

> 

audio_output {
        type            "alsa"
        name            "My ALSA Device"
        device          "hw:0,0"    # optional
#       mixer_type      "hardware"      # optional
#       mixer_device    "default"       # optional
#       mixer_control   "PCM"           # optional
#       mixer_index     "0"             # optional
}





---

### Post by ranperry on 2011-03-17
> **cchhrriiss121212 said:**
> I'm not an MPD user, but I think the crash is related to the multiple channels on the ICE1712 cards (it expects to have a single volume control instead of 12 separate ones). 

Try either or both of these fixes:
[http://www.linuxquestions.org/questions/ubuntu-63/no-sound-in-ubuntu-studio-with-m-audio-delta-44-a-781558/](http://www.linuxquestions.org/questions/ubuntu-63/no-sound-in-ubuntu-studio-with-m-audio-delta-44-a-781558/)
Or this:
[http://ubuntuforums.org/showpost.php?p=9317203&postcount=2](http://ubuntuforums.org/showpost.php?p=9317203&postcount=2)


Some progress....

Adding the following:

```
slave.format S32_LE <---- add this
slave.channels 10 <---- add this
```

Did not help until I have added the following:

```
Code:

 gksudo gedit /etc/modprobe.d/alsa-base.conf

Insert this line at the bottom:
Code:

 options snd-ice1712 model=audiophile


```

Now, I can use MPD with ALSA without crashing it. The problems are:

1. No audio
2. alsamixer crashes with:

```
cannot open mixer: No such file or directory

```

Although it is properly installed.


Any ideas?

---

### Post by tgalati4 on 2011-03-17
ALSA is probably looking for /dev/mixer and it doesn't exist.  What devices do get created in /dev?  Perhaps you can link /dev/mixer for a device that gets created by snd-ice1712 module:

sudo ln -s /dev/mixer /dev/snd/whateversounddevicelooksappropriate

Does envy24control bring up a control panel?  It might be part of alsa-tools-gui.  Do you have that loaded?

sudo apt-get install alsa-tools-gui

---

### Post by ranperry on 2011-03-17
This is the content of /dev/snd/

```
drwxr-xr-x 2 root root      60 2011-03-17 22:35 by-path
crw-rw---- 1 root audio 116, 7 2011-03-17 22:35 controlC0
crw-rw---- 1 root audio 116, 4 2011-03-17 22:35 midiC0D0
crw-rw---- 1 root audio 116, 6 2011-03-17 23:13 pcmC0D0c
crw-rw---- 1 root audio 116, 5 2011-03-17 23:13 pcmC0D0p
crw-rw---- 1 root audio 116, 3 2011-03-17 22:35 seq
crw-rw---- 1 root audio 116, 2 2011-03-17 22:35 timer

```

---

### Post by tgalati4 on 2011-03-18
I presume that pcmC0D0c is for capture and p is for play.  So, you could try:

sudo rm /dev/mixer
sudo ln -s /dev/snd/pcmC0D0p /dev/mixer

ls /dev/m*

---

### Post by ranperry on 2011-03-18
I did as you suggested and rebooted. Still get the same message:

```
Mar 18 09:28 : mixer: Failed to read mixer for 'My ALSA Device': no such mixer control: PCM

```

---

### Post by cchhrriiss121212 on 2011-03-18
You seem to have gone backwards from post #8, where MPD ran successfully. What I would do is get audio working with something simple first, aplay or rhythmbox for example. Once that is verified, move on to MPD. 

I'd also recommend envy24control, navigate to the analogue volume tab to set the levels. DAC means outputs and ADC means inputs, they are muted by default, but all other settings should be OK.

---

### Post by ranperry on 2011-03-18
MPD works fine with Pulseaudio. ALSA is the problem. I have two profiles under MPD, Pusle and ALSA. When I use Pulse, audio is coming out of the card through S/PDIF without a problem. When I try to engage the second profile (ALSA) I get the error in the /var/log/mpd/mpd.log file.

---

### Post by cchhrriiss121212 on 2011-03-18
The error states you just need to set a PCM, which you could do with a custom .asoundrc, something like this (I don't know whether you are after digital or analogue out, this has both):
[http://alsa.opensrc.org/1712_.asoundrc#2007-06-30](http://alsa.opensrc.org/1712_.asoundrc#2007-06-30)

An .asoundrc goes in your /home/username folder, it should not take any restart/reboot to take effect.

---

### Post by ranperry on 2011-03-18
I used the asound file and now I get this when using ALSA through MPD:

```
mpd: /build/buildd/mpd-0.16.1+git20110227.2abad0f/./src/filter/convert_filter_plugin.c:143: convert_filter_set: Assertion `audio_format_valid(out_audio_format)' failed.

```

And when I try to play a FLAC file in aplay, I get this:

```
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
aplay: main:654: audio open error: No such file or directory
```

---

### Post by cchhrriiss121212 on 2011-03-18
Maybe that example was too fancy, try a simpler one:
```

pcm.ice1712 {
type hw     
card 0     
device 0 
} 
ctl.ice1712 {     
type hw     
card 0 
}
```

---

### Post by ranperry on 2011-03-18
Same thing....

```
Mar 18 09:28 : mixer: Failed to read mixer for 'My ALSA Device': no such mixer control: PCM
```

---

### Post by lidex on 2011-03-19
You may need alternate channel mapping:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

---

### Post by laylow45 on 2011-03-19
ranparry

as far as I am concerned ALSA sucks BIG time! I battled with it on Maverick for two weeks and gave up! :( Spend your $50 wisely and get a fully supported OSS Linux Audio driver @ [http://www.opensound.com/]("http://www.opensound.com/")

see my posts on this ALSA crap: [http://ubuntuforums.org/showthread.php?t=1705986](http://ubuntuforums.org/showthread.php?t=1705986)

---

### Post by hai2lp on 2011-03-19
you sure will give $50 if i help you

i think i could help u and remote your PC using Teamviewer

---

### Post by ranperry on 2011-03-19
Does OSS support bit perfect? I need to ensure that I can play hi-res audio files (24/96).

Thanks.

---

### Post by ranperry on 2011-03-19
Solved!!!

This is what I had to use in the mpd.conf file:

```
audio_output {
        type            "alsa"
        name            "My ALSA Device"
        device          "iec958:CARD=M2496,DEV=0"
```

Now it works under ALSA and I get my bit perfect audio to my DAC.

---

### Post by TiberiusT on 2011-06-04
> [cchhrriiss121212;10569783 I'm not an MPD user, but I think the crash is related to the multiple channels on the ICE1712 cards (it expects to have a single volume control instead of 12 separate ones). 

[COLOR=Black]I've edited the /usr/share/alsa/cards/Ice1712.conf
like in this bugfix.
For this you have to open a terminal/konsole and you have to open
*gedit* as ROOT.

**> sudo gedit**
(after enter you have to type in your password!!!)

Than open [/COLOR]the folder:
**/usr/share/alsa/cards/**
find the file **Ice1712.conf** drag an drop it into *gedit*
find these entry like below and insert theses lines lines
(without the <---- add this):


ICE1712.pcm.front.0 {
        @args [ CARD ]
        @args.CARD {
                type string
        }
        type route
        ttable.0.0 1
        ttable.1.1 1
        slave.pcm {
                type hw
                card $CARD
        }
[B]        slave.format S32_LE            <---- add this
        slave.channels 10              <---- add this[/B]
}
Fantastic! I have M-Audio 2496. Alsa 1.024 refused to acknowledge the presence of the Analog Outputs, which were the only ones connected :mad:, so I got no sound. Adding those 2 lines to **/usr/share/alsa/cards/****Ice1712.conf** solved it, and on reboot all options were available in the drop down box on system/preferences/sound/hardware.

I spent ages trying get PulseAudio to load a new analog sink to no avail. I was fooled by using Audacious as a test - under preferences/audio/output Alsa plugin /Plugin Preferences it lists a seperate entry for the card - that would play on Analog Out. I assumed Alsa was working fine but I now assume that Audacious is doing something clever/failsafe with that option.

As an aside, Both Alsa and PulseAudio are seriously excellent - but conversely the docs are woefully inadequate for a new user

T

---

### Post by vmsda on 2011-08-22
I had the same problem. After much battling, the only way I managed to get sound from my Benchmark DAC1 HDR was by omitting the "device" parameter in the "audio_output" section.

MPD says it plays the music at its source resolution: fine. But how can I be sure that ALSA is transferring each resolution unaltered? In fact, when I play a test sound sourced at 24/192 (supplied free by Linn Records), the test comes through with flying colours even through my DAC supports max 24/96 through its USB interface.

---

### Post by TiberiusT on 2011-08-23
> **vmsda said:**
>  when I play a test sound sourced at 24/192 (supplied free by Linn Records), the test comes through with flying colours even through my DAC supports max 24/96 through its USB interface.

Tks for that...I'm gonna check out those files. Easy ref: [http://www.linnrecords.com/linn-downloads-testfiles.aspx](http://www.linnrecords.com/linn-downloads-testfiles.aspx) 

Can't answer your question I'm afraid, but to continue the thread subject I can advise anyone that I have since upgraded to Natty and the Alsa/Pulse contained therein worked out of the box - which rather stunned me considering the hours I spent getting everything to (almost) work in Lucid. Of course the ICE1712 outputs were still muted by default requiring an unmute by running Alsamixer from the terminal - still haven't worked out what's that's all about - kinda like buying a car but the engine won't start by default  - the solution being on page 126 of the manual. :P

T

---

### Post by vmsda on 2011-08-23
> **ranperry said:**
> Solved!!!
... Now it works under ALSA and I get my bit perfect audio to my DAC.

How can you prove that ADWIG (Alsa Delivers What It Gets)? I have a setup functionally comparable to yours, it is finally working but, as per my previous append, I would dearly like to prove to myself that all is working as expected and desired.

---

### Post by TiberiusT on 2011-08-23
> **vmsda said:**
> How can you prove that ADWIG (Alsa Delivers What It Gets)? 

Looks like a question for here:

[https://lists.sourceforge.net/lists/listinfo/alsa-user](https://lists.sourceforge.net/lists/listinfo/alsa-user)

or even here if u use Pulse: 

[http://lists.freedesktop.org/mailman/listinfo/pulseaudio-discuss](http://lists.freedesktop.org/mailman/listinfo/pulseaudio-discuss)

T

---

### Post by Zillode on 2013-03-14
I was struggeling with mpd and digital output (SPDIF) and solved it as follows:

1) aplay -L
```

null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC898 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC898 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC898 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC898 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC898 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC898 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC898 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC898 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
...

```

2) Search for your 'Digital' output (in my case iec958:CARD=PCH,DEV=0)

3) Update your /etc/mpd.conf with your device specification:
audio_output {
        type            "alsa"
        name            "My ALSA Device"
        device          "iec958:CARD=PCH,DEV=0"   # THIS LINE!
        #device         "hw:0,1"        # optional
        #format         "44100:16:2"    # optional
        #mixer_type      "hardware"     # optional
        #mixer_device   "default"       # optional
        #mixer_control  "PCM"           # optional
        #mixer_index    "0"             # optional
}

4) service mpd restart & start playing music

---

### Post by codemaniac on 2013-03-14
Old thread closed now.

---

