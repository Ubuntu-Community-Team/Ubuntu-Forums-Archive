---
title: "HDMI audio in MythTv, but not anywhere else"
date: 2012-11-30
forum: Mythbuntu
---

### Post by lordhedgehog on 2012-11-30
I have an otherwise perfectly working Mythbuntu installation. The only audio output is via HDMI cable to the receiver. My receiver does not accept any other audio inputs when HDMI video is used, so I must get the audio working over HDMI.

Within Mythbuntu, it works fine. Mythbuntu is set to output to "ALSA:hdmi:CARD=Generic,DEV=0"

Outside of Mythbuntu, I get no audio in anything. The output of aplay -D hdmi:0,0 /usr/share/sounds/alsa/Front_Center.wav is:

```

Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
aplay: set_params:1087: Channels count non available

```

The same output is given for aplay -D hw:0,3. Other devices give audio open errors. Using default (or omitting the -D entirely) produces no errors but no sound. The same result occurs if run as sudo.

alsamixer shows all outputs at full volume and unmuted.

My /etc/asound.conf is as follows:

```


pcm.hdmi0 {
        type hw
        card 0
        device 3 }

pcm.!default {
        type  plug
        slave.pcm "hdmi0"
}

pcm.!sysdefault {
        type  plug
        slave.pcm "hdmi0"
}

```

There is no ~/.asoundrc

Under /proc/asound/Generic, I have eld#0.0 with the following contents:

```

monitor_present		1
eld_valid		0

```

I can find no eld_valid 1 in any device.

Audio relevant lines from dmesg are:

```

[    2.883111] snd_hda_intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.883177] snd_hda_intel 0000:00:01.1: irq 54 for MSI/MSI-X
[    2.883201] snd_hda_intel 0000:00:01.1: setting latency timer to 64
[    2.911346] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[    2.911550] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input6
[    2.912202] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.966407] input: HD-Audio Generic Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input7
[    2.966615] input: HD-Audio Generic Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
[    2.966813] input: HD-Audio Generic Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card1/input9
[    2.966901] input: HD-Audio Generic Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
[    2.966975] input: HD-Audio Generic Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
[   18.737823] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=0
[   18.737872] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   18.739270] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=1
[   18.739300] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   19.036030] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   19.336037] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   19.636078] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   19.936123] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   20.236032] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   20.836025] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   21.136059] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[  778.184693] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 1098.953940] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[ 1098.953960] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[ 1098.953988] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[ 1098.954001] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[ 1098.981048] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=0
[ 1098.981077] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[ 1098.982069] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=1
[ 1098.982097] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[ 1099.252108] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[ 1099.552131] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[ 1099.852168] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[ 1100.152172] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[ 1100.452168] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[ 1100.752171] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[ 1101.052170] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[ 1101.352174] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1

```

Output of aplay -L

```

null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
sysdefault
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
front:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    Front speakers
surround40:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    Direct sample mixing device
dmix:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC892 Digital
    Direct sample snooping device
hw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC892 Digital
    Hardware device with all software conversions

```

I've followed every guide and thread I can find that looks relevant. Does anyone have any other suggestions? Why does MythTv work but Chrome, mplayer, aplay, etc., all fail?

---

### Post by lordhedgehog on 2012-12-03
Got it working by switching to PulseAudio. So far no issues.

```

sudo apt-get install libasound2-plugins "pulseaudio-*" paman paprefs pavucontrol pavumeter

```

---

