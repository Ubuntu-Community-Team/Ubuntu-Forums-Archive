---
title: "Problem with pulseaudio showing only 2 input channels"
date: 2020-10-19
forum: Multimedia Software
---

### Post by sevland2020 on 2020-10-19
Hello everybody,

i want to use a MixPre-10 II (from Sound Device) to capture multiple microphones (up to 5 or 6) at the same time and analyze the signals on a computer.
The MixPre-10 II is connected via USB-C to a pc running Ubuntu OS and a python script including pyaudio to capture the multiple channels.

The problem is that pavucontrol (and Audacity e.g.) only shows 2 input channels.

The MixPre-10 II is configured correctly, because on a Mac OS every 12 input channels are shown.

'pacmd list-sources' produces the following output:
```

 * index: 11
    name: <alsa_input.usb-Sound_Devices__LLC_MixPre-10_II_TJ0120085001-00.iec958-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9048
    volume: front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max rewind: 0 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 2000,00 ms
    card: 6 <alsa_card.usb-Sound_Devices__LLC_MixPre-10_II_TJ0120085001-00>
    module: 33
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "USB Audio"
        alsa.id = "USB Audio"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "MixPre-10 II"
        alsa.long_card_name = "Sound Devices, LLC MixPre-10 II at usb-0000:00:14.0-3, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:3:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/sound/card1"
        udev.id = "usb-Sound_Devices__LLC_MixPre-10_II_TJ0120085001-00"
        device.bus = "usb"
        device.vendor.id = "0926"
        device.vendor.name = "Sound Devices, LLC"
        device.product.id = "0210"
        device.product.name = "MixPre-10 II"
        device.serial = "Sound_Devices__LLC_MixPre-10_II_TJ0120085001"
        device.string = "iec958:1"
        device.buffering.buffer_size = "352800"
        device.buffering.fragment_size = "176400"
        device.access_mode = "mmap+timer"
        device.profile.name = "iec958-stereo"
        device.profile.description = "Digital Stereo (IEC958)"
        device.description = "MixPre-10 II Digital Stereo (IEC958)"
        alsa.mixer_name = "USB Mixer"
        alsa.components = "USB0926:0210"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    ports:
        iec958-stereo-input: Digital Input (S/PDIF) (priority 0, latency offset 30000 usec, available: unknown)
            properties:
                
    active port: <iec958-stereo-input>

```

If i change the soundcard to MixPre-10 II in alsamixer, the message "This sound device does not have any controls" appears.

I suspect it has something to do with PulseAudio, but as I have very little experience in this field, I wanted to ask if anyone had a similar problem or has any idea how to face the problem.

Many thanks in advance!

---

### Post by Autodave on 2020-10-19
I don't know anything about that unit, but does Audacity recognize it?  You need to go to Edit -> Preferences -> Devices -> Recording.  That's how I get to our 32 channel mixer.

---

### Post by sevland2020 on 2020-10-21
Audacity recognize it, but only 2 channels.

Does your 32 channel mixer appears as a 32 channel mixer in your system sound settings?

Edit: Running Ubuntu 18.04.5 if it is important.

---

### Post by Autodave on 2020-10-21
Our mixer is an Allen & Heath QU32.  In Audacity it comes up as "QU32".  Also, while still in Audacity, either in Preferences (where you were previously) or on the main screen, there is a place for you to chose the number of channels.  If I am only using the first 15 channels of the mixer, I can just set Audacity to only record 15 channels on the main screen.

---

### Post by sevland2020 on 2020-10-26
The problem is that i can only choose between 1 and 2 channel in Audacity because the system itself recognize the device as 2 in / 2 out.

---

### Post by Autodave on 2020-10-26
And Audacity does recognize the unit correctly?

---

### Post by sevland2020 on 2020-10-27
No. Audacity recognize the unit as 2 in / 2 out like ALSA does.

---

### Post by Autodave on 2020-10-27
But, does Audacity recognize it as a MixPre-10 II?  File -> Preferences -> Devices -> Recording.  In that box, you *should* be able to click on it and see all the possibilities.  For instance on my 32 channel mixer, when I click on that box I get QU32 32 different ways: 1 channel, 2, channels, 3 channels, 4 channels, etc. all the way up to QU32 32 channels.

---

### Post by sevland2020 on 2020-11-02
Sorry for the late answer.

Audacity recognize it as a MixPre-10 II, but under File -> Preferences -> Devices -> Recording only 2 channels are available.
The problem does not lie with audacity, but with ALSA I think.

---

### Post by CelticWarrior on 2020-11-02
There's a [comment]("https://discourse.ardour.org/t/sound-devices-mixpre-d-usb/90499/3") at Ardour forums that may or may not be relevant:

> [COLOR=#000000][FONT=Helvetica]it is necessary to run the MixPre-D in &#8220;full-speed&#8221; USB mode. To do this, hold down the[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Headphone Controller while inserting the USB plug to the MixPre-D.[/FONT][/COLOR]

---

### Post by Autodave on 2020-11-02
That was going to be my next guess.  NOT!  How in the world did you find that and how would anyone know to do that?  Amazing.  Well done, sir!  (Well done even if it doesn't fix the problem!)

---

### Post by sevland2020 on 2020-11-10
> **CelticWarrior said:**
> There's a [comment]("https://discourse.ardour.org/t/sound-devices-mixpre-d-usb/90499/3") at Ardour forums that may or may not be relevant:

Thanks for the reference but the device is already running in highspeed mode.

Actually I didn't found any way to make the device running with more than 2 in / 2 out with ubuntu / win 10.
So I need to buy a new one.

Anyway, thanks for the help!

---

