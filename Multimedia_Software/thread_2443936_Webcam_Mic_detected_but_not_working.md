---
title: "Webcam Mic detected but not working"
date: 2020-05-22
forum: Multimedia Software
---

### Post by ddav on 2020-05-22
Hi, 

I just got a webcam with built in MIC but cannot get the MIC to work.

I've confirm the webcam and mic work correctly on another windows laptop. 

The Mic is available for selection in input devices but the sound bar never increases. 

I have a USB headset which works with no issues. 

I gone through all the usual checks and threads but to no avail.


Some more info:

Linux dave-HP-Z210-Workstation 5.3.0-53-generic #47~18.04.1-Ubuntu SMP Thu May 7 13:10:50 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

index: 18
    name: <alsa_input.usb-Logitech_Logitech_USB_Headset-00.analog-mono>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: 
    priority: 9049
    volume: mono: 53971 /  82% / -5.06 dB
            balance 0.00
    base volume: 21535 /  33% / -29.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 0 KiB
    sample spec: s16le 1ch 44100Hz
    channel map: mono
                 Mono
    used by: 1
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 2000.00 ms
    card: 14 <alsa_card.usb-Logitech_Logitech_USB_Headset-00>
    module: 42
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
        alsa.card = "3"
        alsa.card_name = "Logitech USB Headset"
        alsa.long_card_name = "Logitech Logitech USB Headset at usb-0000:00:1d.0-1.7, full speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:1d.0-usb-0:1.7:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7:1.0/sound/card3"
        udev.id = "usb-Logitech_Logitech_USB_Headset-00"
        device.bus = "usb"
        device.vendor.id = "046d"
        device.vendor.name = "Logitech, Inc."
        device.product.id = "0a0c"
        device.product.name = "Clear Chat Comfort USB Headset"
        device.serial = "Logitech_Logitech_USB_Headset"
        device.form_factor = "headset"
        device.string = "hw:3"
        device.buffering.buffer_size = "176400"
        device.buffering.fragment_size = "88200"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-mono"
        device.profile.description = "Analog Mono"
        device.description = "Clear Chat Comfort USB Headset Analog Mono"
        alsa.mixer_name = "USB Mixer"
        alsa.components = "USB046d:0a0c"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-headset-usb"
        device.intended_roles = "phone"
    ports:
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
    active port: <analog-input-mic>


So MIC seems to be picked up and is running, just no input sound bar in the sound app. 

Heres the webcam - [https://www.amazon.co.uk/gp/product/B087TLGRC4/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B087TLGRC4/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1)

Any help would be great.

Thanks,
Dave.

---

### Post by speartip on 2020-05-22
I know it's a bit late now, but looking at some of the customer reviews, I would have avoided that product like the plague. Scanning down many customers have commented on audio problems. 
What program are you using it with? Zoom, Skype etc....

---

### Post by ddav on 2020-05-22
yeah, just zoom and skype. 
Not a big deal, Ill just pick up a cheap mic and plug it into the audio jack.

Just annoying me that is does not work :)

---

### Post by TheFu on 2020-05-22
If you are using PulseAudio, Pulse likes to make the last connected device work.  This means that the simple answer often is to unplug the USB device, then plug it back in. Wait 5 seconds, then launch the program you'd like to use with the cam+mic and pick it from the list.

I have a Logitech C920 webcam+mic.  Some times it is flaky with certain setups, usually after I've used or changed some audio settings in pavucontrol.  Someone else here posted some shell commands to make setup a little easier and they've worked for a few people here and trying to join some weekly meetings that I run.

# Get a list of sources (microphones), look for Logitech, if that's the maker.
```
$ pacmd list-sources | egrep '\.name|name:|port|state'
```

#   Use the "name: <xxxxxxx>" part from the output above, below, for example:
```
$ pacmd set-default-source alsa_input.usb-046d_HD_Pro_Webcam_C920_76xxx93F-02.analog-stereo
```
If the microphone doesn't show up in the first command output, then it needs to be enabled (not off) from **pavucontrol**, in the far right tab.

This assumes that the driver for both the video and mic are loaded and working.  That's a harder thing, but **lshw** can be used to check.

---

### Post by speartip on 2020-05-22
If you're using Zoom. Go to Zoom's audio settings. Make sure the device you're using is selected. (In mine it wasn't, I had to change it). Also my Mic volume defaults to 0% in Zoom, I have to move the slider right across.

---

### Post by ddav on 2020-05-23
Thanks for the feedback. 

I've tried all the usual steps to get it working and still nothing :(

TheFu tried your suggestion as well. 

Th thing is, the MIC is getting picked up by the system and everythings "looks" good. I can see the MIC as an option in every application. 

Heres the output of the pacmd

```

* index: 3
    name: <alsa_input.usb-GENERAL_GENERAL_WEBCAM-02.analog-mono>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: 
    priority: 9049
    volume: mono: 54527 /  83% / -4.79 dB
            balance 0.00
    base volume: 9619 /  15% / -50.00 dB
    volume steps: 65537
    muted: no
    current latency: 74072.24 ms
    max rewind: 0 KiB
    sample spec: s16le 1ch 16000Hz
    channel map: mono
                 Mono
    used by: 1
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 2000.00 ms
    card: 3 <alsa_card.usb-GENERAL_GENERAL_WEBCAM-02>
    module: 31
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
        alsa.card = "2"
        alsa.card_name = "GENERAL WEBCAM"
        alsa.long_card_name = "GENERAL GENERAL WEBCAM at usb-0000:00:1a.0-1.5, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:1a.0-usb-0:1.5:1.2"
        sysfs.path = "/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.2/sound/card2"
        udev.id = "usb-GENERAL_GENERAL_WEBCAM-02"
        device.bus = "usb"
        device.vendor.id = "1b3f"
        device.vendor.name = "Generalplus Technology Inc."
        device.product.id = "2002"
        device.product.name = "808 Camera"
        device.serial = "GENERAL_GENERAL_WEBCAM"
        device.form_factor = "webcam"
        device.string = "hw:2"
        device.buffering.buffer_size = "64000"
        device.buffering.fragment_size = "32000"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-mono"
        device.profile.description = "Analog Mono"
        device.description = "808 Camera Analog Mono"
        alsa.mixer_name = "USB Mixer"
        alsa.components = "USB1b3f:2002"
        module-udev-detect.discovered = "1"
        device.icon_name = "camera-web-usb"
    ports:
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
    active port: <analog-input-mic>

```

You can see the Mic is picked up, RUNNING state etc.

Anyway, Ill keep trying but may be returning this one!!!

---

### Post by drjdmartin on 2020-05-23
Not sure whether this is helpful but...

I've noticed my cam's mic is working but often gets muted - when it mutes if I go into pavucontrol and put the sound to 100% or higher it works. But if the mic gets a louder noise its like the system decides to automatically reduce the volume, and any volume under 100% in pavucontrol is practically muted so it makes it seem like it isn't working.

---

### Post by TheFu on 2020-05-23
pacmd puts out too much information to be useful unless you are a pa dev.  That's why I provided the specific command with a grep filter - to only see what was important.

---

### Post by ddav on 2020-05-23
Heres the output of the pacmd commno piped to egrep

```

$ pacmd list-sources | egrep '\.name|name:|port|state'
    name: <alsa_input.usb-GENERAL_GENERAL_WEBCAM-02.analog-mono>
    state: SUSPENDED
        alsa.name = "USB Audio"
        device.vendor.name = "Generalplus Technology Inc."
        device.product.name = "808 Camera"
        device.profile.name = "analog-mono"
    ports:
    active port: <analog-input-mic>
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
    state: SUSPENDED
        device.vendor.name = "Intel Corporation"
        device.product.name = "6 Series/C200 Series Chipset Family High Definition Audio Controller"
    name: <alsa_input.pci-0000_00_1b.0.analog-stereo>
    state: SUSPENDED
        alsa.name = "ALC262 Analog"
        device.vendor.name = "Intel Corporation"
        device.product.name = "6 Series/C200 Series Chipset Family High Definition Audio Controller"
        device.profile.name = "analog-stereo"
    ports:
    active port: <analog-input-front-mic>
dave@dave-HP-Z210-Workstation:~$ pacmd list-sources | egrep '\.name|name:|port|state'
    name: <alsa_input.usb-GENERAL_GENERAL_WEBCAM-02.analog-mono>
    state: RUNNING
        alsa.name = "USB Audio"
        device.vendor.name = "Generalplus Technology Inc."
        device.product.name = "808 Camera"
        device.profile.name = "analog-mono"
    ports:
    active port: <analog-input-mic>
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
    state: SUSPENDED
        device.vendor.name = "Intel Corporation"
        device.product.name = "6 Series/C200 Series Chipset Family High Definition Audio Controller"
    name: <alsa_input.pci-0000_00_1b.0.analog-stereo>
    state: SUSPENDED
        alsa.name = "ALC262 Analog"
        device.vendor.name = "Intel Corporation"
        device.product.name = "6 Series/C200 Series Chipset Family High Definition Audio Controller"
        device.profile.name = "analog-stereo"
    ports:
    active port: <analog-input-front-mic>

```

Tried 

pacmd set-default-source alsa_input.usb-GENERAL_GENERAL_WEBCAM-02.analog-mono

 but same issue

---

### Post by TheFu on 2020-05-23
Would really be helpful if you use code tags, please, please.

There are too many input choices. Go into pavucontrol and disable "off" the mics you don't want used or just unplug them from the machine.  

```
$ pacmd list-sources | egrep '\.name|nameport|state'
name: <alsa_input.usb-GENERAL_GENERAL_WEBCAM-02.analog-mono>
state: RUNNING
```

Looks like the alsa_input.usb-GENERAL_GENERAL_WEBCAM-02.analog-mono is the current microphone and active. 

OTOH, sometimes crap hardware is just crap hardware.

---

### Post by lordrahl007 on 2020-07-13
I am having the same problem, with a different webcam.  I bought this  one specifically because one of the reviews states he is running "the  latest version" of Kubuntu and it works on his system.

[https://smile.amazon.com/gp/product/B088D3VXC6/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1](https://smile.amazon.com/gp/product/B088D3VXC6/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1)

The mic  shows up in pavucontrol in inputs, and when I open zoom it pops up in  the Recording pane in pavucontrol.  So it is being recognized, and the  volume bar is all the way up on zoom and at 100% in pavucontrol, but it  simply is not receiving any audio.

The pacmd shows the mic is  recognized and is in a Running state.  By all accounts that I can see,  this thing SHOULD be working.  The video does work, and the video and  audio do work on my Win10 machine.

```
$ pacmd list-sources | egrep '\.name|name:|port|state'
        name: <alsa_output.pci-0000_02_02.0.analog-stereo.monitor>
        state: SUSPENDED
                device.vendor.name = "Ensoniq"
                device.product.name = "ES1371/ES1373 / Creative Labs CT2518 (Audio PCI 64V/128/5200 / Creative CT4810/CT5803/CT5806 [Sound Blaster PCI])"
        name: <alsa_input.usb-Ingenic_Semiconductor_CO.__LTD._HD_Web_Camera_Ucamera001-02.analog-mono>
        state: RUNNING
                alsa.name = "USB Audio"
                device.vendor.name = "ARC International"
                device.product.name = "Camera"
                device.profile.name = "analog-mono"
        ports:
        active port: <analog-input-mic>
```

---

### Post by rafe101 on 2020-07-18
I had the exact same problem: detected, but not showing any input. I literally just changed how it was plugged in and it worked. It was originally connected through a little port on the top of my desk and I plugged the cable in directly and, just like that, everything was fine.

---

### Post by peterbcs on 2021-01-21
> **drjdmartin said:**
> Not sure whether this is helpful but...

I've noticed my cam's mic is working but often gets muted - when it mutes if I go into pavucontrol and put the sound to 100% or higher it works. But if the mic gets a louder noise its like the system decides to automatically reduce the volume, and any volume under 100% in pavucontrol is practically muted so it makes it seem like it isn't working.

Thank you! This was exactly my problem. Even the slightest bit under 100% and the mic is off.

---

### Post by olieth on 2021-01-28
Hi there!

I'm experiencing a similar issue: The internal microphone of my new webcam does not work (the camera  itself does). The mic gets detected (USB PHY 2.0), shows up in pavucontrol as input  device, in the configuration tag the profiles mono and  multichannel-input are available. Both do not work and strangely there  is no input level indicator as I see at the (working) internal mic. It  is available in the audio configuration with two entries (mono and  multichannel) neither of which work
 ```

$ pacmd list-sources | egrep '\.name|name:|port|state'
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
    state: IDLE
        device.vendor.name = "Intel Corporation"
        device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
    name: <alsa_input.pci-0000_00_1b.0.analog-stereo>
    state: IDLE
        alsa.name = "92HD75B3X5 Analog"
        device.vendor.name = "Intel Corporation"
        device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
        device.profile.name = "analog-stereo"
    ports:
    active port: <analog-input-internal-mic>
    name: <alsa_input.usb-Jieli_Technology_USB_PHY_2.0-02.multichannel-input>
    state: RUNNING
        alsa.name = "USB Audio"
        device.vendor.name = "Jieli Technology"
        device.product.name = "USB PHY 2.0"
        device.profile.name = "multichannel-input"
    ports:
    active port: <multichannel-input>

```

I already checked alsamixer, pavucontrol (as mentioned above), the  "snd-usb-audio"-modprobe and searched various forums without finding a  solution. The webcam works on a WIN10 machine. Does anyone have an idea  on how to fix this?

Thank you for your help!
olieth

---

