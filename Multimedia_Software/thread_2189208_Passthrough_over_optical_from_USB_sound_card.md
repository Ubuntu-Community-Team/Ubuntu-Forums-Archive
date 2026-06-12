---
title: "Passthrough over optical from USB sound card"
date: 2013-11-21
forum: Multimedia Software
---

### Post by matzie on 2013-11-21
I've been trying to get 5.1 DD/DTS passthrough from a USB sound card to an AV receiver over an optical cable for a very long time.  I've read countless tutorials and followed innumerable guides but can't get anywhere.  I've never been able to get PA to list any optical output except iec958-stereo, and I've never found an alsa control for optical output listed (there's an spdif input, which I've tried  toggling) . I can get front left and right over optical to work fine, but sending a dolby trailer bob to it from mplayer givs static.  

I'm open to the prospect that neither of the two cards I've tried are properly supported, but I don't want to waste money on another only to have the same problem again. 

The card I'm using now appears in lsusb as:

Bus 004 Device 002: ID 0d8c:0102 C-Media Electronics, Inc. CM106 Like Sound Device

aplay -L says:

```
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Device
    USB Sound Device, USB Audio
    Default Audio Device
front:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Front speakers
surround40:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Direct sample mixing device
dsnoop:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Direct sample snooping device
hw:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Direct hardware device without any conversions
plughw:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Hardware device with all software conversions

```

pavucontrol doesn't list the 'Digital Surround 5.1 iec958' type profile I thought should be there.

pacmd list-cards says:

```

>>> 1 card(s) available.
    index: 1
    name: <alsa_card.usb-0d8c_USB_Sound_Device-00-Device>
    driver: <module-alsa-card.c>
    owner module: 23
    properties:
        alsa.card = "0"
        alsa.card_name = "USB Sound Device"
        alsa.long_card_name = "USB Sound Device at usb-0000:00:12.0-3, full speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:12.0-usb-0:3:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/sound/card0"
        udev.id = "usb-0d8c_USB_Sound_Device-00-Device"
        device.bus = "usb"
        device.vendor.id = "0d8c"
        device.vendor.name = "C-Media Electronics, Inc."
        device.product.id = "0102"
        device.product.name = "CM106 Like Sound Device"
        device.serial = "0d8c_USB_Sound_Device"
        device.string = "0"
        device.description = "CM106 Like Sound Device"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    profiles:
        input:analog-stereo: Analogue Stereo Input (priority 10, available: unknown)
        input:iec958-stereo: Digital Stereo (IEC958) Input (priority 5, available: unknown)
        output:analog-stereo: Analogue Stereo Output (priority 1000, available: unknown)
        output:analog-stereo+input:analog-stereo: Analogue Stereo Duplex (priority 1010, available: unknown)
        output:analog-stereo+input:iec958-stereo: Analogue Stereo Output + Digital Stereo (IEC958) Input (priority 1005, available: unknown)
        output:analog-surround-40: Analogue Surround 4.0 Output (priority 700, available: unknown)
        output:analog-surround-40+input:analog-stereo: Analogue Surround 4.0 Output + Analogue Stereo Input (priority 710, available: unknown)
        output:analog-surround-40+input:iec958-stereo: Analogue Surround 4.0 Output + Digital Stereo (IEC958) Input (priority 705, available: unknown)
        output:analog-surround-41: Analogue Surround 4.1 Output (priority 800, available: unknown)
        output:analog-surround-41+input:analog-stereo: Analogue Surround 4.1 Output + Analogue Stereo Input (priority 810, available: unknown)
        output:analog-surround-41+input:iec958-stereo: Analogue Surround 4.1 Output + Digital Stereo (IEC958) Input (priority 805, available: unknown)
        output:analog-surround-50: Analogue Surround 5.0 Output (priority 700, available: unknown)
        output:analog-surround-50+input:analog-stereo: Analogue Surround 5.0 Output + Analogue Stereo Input (priority 710, available: unknown)
        output:analog-surround-50+input:iec958-stereo: Analogue Surround 5.0 Output + Digital Stereo (IEC958) Input (priority 705, available: unknown)
        output:analog-surround-51: Analogue Surround 5.1 Output (priority 3800, available: unknown)
        output:analog-surround-51+input:analog-stereo: Analogue Surround 5.1 Output + Analogue Stereo Input (priority 3810, available: unknown)
        output:analog-surround-51+input:iec958-stereo: Analogue Surround 5.1 Output + Digital Stereo (IEC958) Input (priority 3805, available: unknown)
        output:analog-surround-71: Analog Surround 7.1 Output (priority 700, available: unknown)
        output:analog-surround-71+input:analog-stereo: Analog Surround 7.1 Output + Analogue Stereo Input (priority 710, available: unknown)
        output:analog-surround-71+input:iec958-stereo: Analog Surround 7.1 Output + Digital Stereo (IEC958) Input (priority 705, available: unknown)
        output:iec958-stereo: Digital Stereo (IEC958) Output (priority 500, available: unknown)
        output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analogue Stereo Input (priority 510, available: unknown)
        output:iec958-stereo+input:iec958-stereo: Digital Stereo Duplex (IEC958) (priority 505, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:iec958-stereo>
    sinks:
        alsa_output.usb-0d8c_USB_Sound_Device-00-Device.iec958-stereo/#2: CM106 Like Sound Device Digital Stereo (IEC958)
    sources:
        alsa_output.usb-0d8c_USB_Sound_Device-00-Device.iec958-stereo.monitor/#2: Monitor of CM106 Like Sound Device Digital Stereo (IEC958)
    ports:
        analog-input-microphone: Microphone (priority 8700, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: unknown)
            properties:


        iec958-stereo-input: Digital Input (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:


        iec958-stereo-output: Digital Output (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:

```

The machine is an HP Microserver N40L with no onboard sound.  It's running a vanilla 13.10 install at the moment.  On previous installs I've tried removing pulseaudio, tried the a52 plugin, tried so many things... but no luck ever. 

Would really appreciate any help or pointers you can give!  Just uploaded alsa-info output to [http://www.alsa-project.org/db/?f=b47b30039569989aa0628b1f837d78f9d7f40804](http://www.alsa-project.org/db/?f=b47b30039569989aa0628b1f837d78f9d7f40804)  Also very open if this card, or the other one I have, a Behringer UCA-222, can't do what I want, to buying another.  (The Behringer only has a single control listed in alsamixer, "PCM")  Edit: Also happy to look at a PCIe card, if there's one that's known to work for what I need.


Thanks in advance for any help you can give!

---

