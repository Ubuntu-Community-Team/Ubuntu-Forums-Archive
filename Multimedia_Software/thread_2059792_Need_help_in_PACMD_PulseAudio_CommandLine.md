---
title: "Need help in PACMD PulseAudio CommandLine"
date: 2012-09-18
forum: Multimedia Software
---

### Post by XsheepX on 2012-09-18
Hi,
Remember when Ubuntu used to come with pavucontrol and it allowed you to change the built-in audio profile between Analog Stereo Duplex and Analog Stereo Output? Yeah, that was a really cool feature that allowed users to have audio coming out of their speakers be routed as input for their microphones.

Anyway, I have another distro that *refuses* to run pavucontrol, due to dependency s****.
So, I ask you, my Linux brethren, how does one go about changing the card profile between Analog Stereo Output/Duplex in terminal using pacmd?

Here is my output from pacmd list-cards
```

sheep@sheep-HP:~$ pacmd list-cards
Welcome to PulseAudio! Use "help" for usage information.
>>> 1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1b.0>
    driver: <module-alsa-card.c>
    owner module: 4
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel"
        alsa.long_card_name = "HDA Intel at 0xdc800000 irq 50"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.name = "82801I (ICH9 Family) HD Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        output:analog-stereo: Analog Stereo Output (priority 6000)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060)
        output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400)
        output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analog Stereo Input (priority 5460)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300)
        output:hdmi-surround+input:analog-stereo: Digital Surround 5.1 (HDMI) Output + Analog Stereo Input (priority 360)
        input:analog-stereo: Analog Stereo Input (priority 60)
        off: Off (priority 0)
    active profile: <output:analog-stereo+input:analog-stereo>
    sinks:
        alsa_output.pci-0000_00_1b.0.analog-stereo/#0: Built-in Audio Analog Stereo
    sources:
        alsa_output.pci-0000_00_1b.0.analog-stereo.monitor/#0: Monitor of Built-in Audio Analog Stereo
        alsa_input.pci-0000_00_1b.0.analog-stereo/#1: Built-in Audio Analog Stereo
    ports:
        analog-output-speaker: Speakers (priority 10000, available: unknown)
            properties:
                
        analog-output-headphones: Headphones (priority 9000, available: unknown)
            properties:
                
        analog-input-microphone-internal: Internal Microphone (priority 8900, available: no)
            properties:
                
        analog-input-microphone: Microphone (priority 8700, available: yes)
            properties:
                
        analog-input-linein: Line In (priority 8100, available: unknown)
            properties:
                
        hdmi-output-0: HDMI / DisplayPort (priority 5900, available: no)
            properties:
                
>>> sheep@sheep-HP:~$

```So I tried setting the card profile for the Analog Output Duplex, and got this:
```

sheep@sheep-HP:~$ pacmd set-card-profile analog-stereo+input
Welcome to PulseAudio! Use "help" for usage information.
>>> You need to specify a profile by its name.
>>> sheep@sheep-HP:~$ 

```
I guess I'm not specifying the profile name correctly? I tried loading the module with pacmd load-module analog-stereo+input and it told me module failed to load...

There is a list of commands at [http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/CLI](http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/CLI)

Any help would be much appreciated! :)

---

