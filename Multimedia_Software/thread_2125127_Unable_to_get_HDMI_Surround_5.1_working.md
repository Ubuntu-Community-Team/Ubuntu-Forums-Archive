---
title: "Unable to get HDMI Surround 5.1 working"
date: 2013-03-13
forum: Multimedia Software
---

### Post by 0x4e on 2013-03-13
I am working on setting up an HTPC running Ubuntu 12.10.  I have been searching for hours for a solution to get 5.1 surround sound working through HDMI, to no avail.  I do not know a lot about audio standards or how they are managed in Linux.  Right now, I am able to get what I think is 2 channel audio through HDMI.

In PulseAudio Volume Control, I only get the following two profile options for HDMI:
[LIST]
[*]Digital Stereo (HDMI) Output + Analog Stereo Input
[*]Digital Stereo (HDMI) Output
[/LIST]

The computer is connected via HDMI to the TV which in turn is connected to the speaker system.

Possibly relevant computer specs:
[LIST]
[*]Shuttle XH61V (Intel H61 Chipset)
[*]Onboard Realtek ALC662 5.1 channel High Definition Audio
[*]Intel Core i3-3225 with Intel HD Graphics 4000
[/LIST]

Being as the HDMI is built into the motherboard, I don't really know whether the ALC662, the motherboard or the Intel Graphics is controlling it.

I have tried running "speaker-test -c 6" and Front Left, Center, Front Right all produce static but Rear Right, Rear Left and LFE all either silent or are much quieter.

pacmd list-cards gives me the following:
```

Welcome to PulseAudio! Use "help" for usage information.
>>> 1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1b.0>
    driver: <module-alsa-card.c>
    owner module: 4
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf7d00000 irq 51"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.name = "6 Series/C200 Series Chipset Family High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        output:analog-stereo: Analog Stereo Output (priority 6000)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060)
        output:analog-surround-40: Analog Surround 4.0 Output (priority 700)
        output:analog-surround-40+input:analog-stereo: Analog Surround 4.0 Output + Analog Stereo Input (priority 760)
        output:analog-surround-41: Analog Surround 4.1 Output (priority 800)
        output:analog-surround-41+input:analog-stereo: Analog Surround 4.1 Output + Analog Stereo Input (priority 860)
        output:analog-surround-50: Analog Surround 5.0 Output (priority 700)
        output:analog-surround-50+input:analog-stereo: Analog Surround 5.0 Output + Analog Stereo Input (priority 760)
        output:analog-surround-51: Analog Surround 5.1 Output (priority 800)
        output:analog-surround-51+input:analog-stereo: Analog Surround 5.1 Output + Analog Stereo Input (priority 860)
        output:iec958-stereo: Digital Stereo (IEC958) Output (priority 5500)
        output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (priority 5560)
        output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400)
        output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analog Stereo Input (priority 5460)
        input:analog-stereo: Analog Stereo Input (priority 60)
        off: Off (priority 0)
    active profile: <output:hdmi-stereo+input:analog-stereo>
    sinks:
        alsa_output.pci-0000_00_1b.0.hdmi-stereo/#0: Built-in Audio Digital Stereo (HDMI)
    sources:
        alsa_output.pci-0000_00_1b.0.hdmi-stereo.monitor/#0: Monitor of Built-in Audio Digital Stereo (HDMI)
        alsa_input.pci-0000_00_1b.0.analog-stereo/#1: Built-in Audio Analog Stereo
    ports:
        analog-output: Analog Output (priority 9900, available: unknown)
            properties:
                
        analog-output-headphones: Headphones (priority 9000, available: no)
            properties:
                
        analog-input-microphone-front: Front Microphone (priority 8500, available: no)
            properties:
                
        analog-input-microphone-rear: Rear Microphone (priority 8200, available: no)
            properties:
                
        analog-input-linein: Line In (priority 8100, available: no)
            properties:
                
        iec958-stereo-output: Digital Output (S/PDIF) (priority 0, available: unknown)
            properties:
                
        hdmi-output-0: HDMI / DisplayPort (priority 5900, available: yes)
            properties:

```

And aplay -L gives me this:
```

default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC662 rev1 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC662 rev1 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC662 rev1 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC662 rev1 Digital
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC662 rev1 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC662 rev1 Digital
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC662 rev1 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC662 rev1 Digital
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC662 rev1 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC662 rev1 Digital
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions

```


Thank you in advance for any help on this!

---

### Post by 0x4e on 2013-03-15
Anyone have any advice on this?  Unfortunately I still haven't got anywhere.  I tried installing the Ubuntu 13.04 nightly build, but it seems to present the exact same problem.

---

### Post by csowm5je on 2013-03-21
I spend three days trying to get the HDMI 5.1 working with no luck. I tried all 12.04,12.10,13.04 beta, MythUbuntu, XBMC. Ordered the Nvidia 210 but I see some thread with "Not working". Installing the XP(over 10 year old operating system) now. Hope to watch some Bluray, DVD and collection of 100s of music vidoes instead of trying to fix and wasting time.

---

### Post by papibe on 2013-03-21
Hi 0x4e.

It looks like your system supports 5.1 only through the analog connections.

Note that this doesn't mean that a program, like say, XBMC, can reproduce 5.1 audio by down mixing it on the fly to stereo. 

Regards.

---

### Post by vaderj on 2013-03-21
for getting audio to work through my radeon hdmi, i had to change the following in my /etc/default/grub file from:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

you obviously dont have a radeon, but it might be worth looking into

---

### Post by Xolture on 2013-04-30
Try this, might works:

sudo nano /etc/pulse/daemon.conf

change these lines:

default-sample-channels = 6
enable-lfe-remixing = yes

OPTIONAL

sudo nano /etc/modprobe.d/alsa-base.conf

add this line at the end of the file:

options snd-hda-intel model=3stack-6ch-dig


Don't forget to reboot after editing,  go to pulseaudio settings to select 5.1 hdmi output, and GOODLUCK

---

### Post by SeijiSensei on 2013-04-30
If you are routing the audio through the TV before it reaches the receiver, that may be the problem.  My Sony Bravia doesn't pass through 5.1, and a bit of research suggests this is a common feature.  It has to do with HDCP, the encryption system that protects high-definition audio and video sources.  Because the path between the TV and the receiver isn't "protected," meaning that it isn't encrypted, the TV strips out the HD audio and just passes Stereo 2.0.

If you can connect the HDMI out to the receiver first, and then pass the video to the TV, you might have better results.

---

### Post by SeijiSensei on 2013-04-30
> **0x4e said:**
> The computer is connected via HDMI to the TV which in turn is connected to the speaker system.
If you are routing the audio through the TV before it reaches the receiver, that may be the problem.  My Sony Bravia doesn't pass through 5.1, and a bit of research suggests this is a common feature.  It has to do with HDCP, the encryption system that protects high-definition audio and video sources.  Because the path between the TV and the receiver isn't "protected," meaning that it isn't encrypted, the TV strips out the HD audio and just passes Stereo 2.0.

If you can connect the HDMI out to the receiver first, and then pass the video to the TV, you might have better results.

---

### Post by gordintoronto on 2013-04-30
+1 for SeijiSensei!

---

