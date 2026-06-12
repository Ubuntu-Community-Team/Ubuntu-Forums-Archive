---
title: "Internal microphone not recognized in ALSA"
date: 2023-12-02
forum: Multimedia Software
---

### Post by bimmelbommel on 2023-12-02
Hi there,
I just bought a Lenovo IdeaPad Pro 5 (16ARP8) and installed Ubuntu 22.04.3. Everything is working fine until I tried to hop onto a call and noticed that the internal microphone doesn't work and in fact isn't recognized by the system at all.

[IMG]https://i.stack.imgur.com/0bMAl.png[/IMG]

After some research I found a thread in an Arch forum with basically the exact same problem: [https://bbs.archlinux.org/viewtopic.php?id=278886](https://bbs.archlinux.org/viewtopic.php?id=278886)

Here's my output:
```

    lspci | grep Audio
    73:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1640 <-- HDMI
    73:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor (rev 60) <- internal microphone
    73:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller <-- Speakers/Headphone jack

    inxi -Axxx
    Audio:
      Device-1: AMD vendor: Lenovo driver: snd_hda_intel v: kernel pcie:
        speed: 16 GT/s lanes: 16 bus-ID: 73:00.1 chip-ID: 1002:1640 class-ID: 0403
      Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
        vendor: Lenovo driver: snd_pci_acp6x v: kernel pcie: speed: 16 GT/s
        lanes: 16 bus-ID: 73:00.5 chip-ID: 1022:15e2 class-ID: 0480
      Device-3: AMD Family 17h HD Audio vendor: Lenovo driver: snd_hda_intel
        v: kernel pcie: speed: 16 GT/s lanes: 16 bus-ID: 73:00.6 chip-ID: 1022:15e3
        class-ID: 0403
      Sound Server-1: ALSA v: k6.2.0-37-generic running: yes
      Sound Server-2: PulseAudio v: 15.99.1 running: yes
      Sound Server-3: PipeWire v: 0.3.48 running: yes 
```

And I think this is the problem. I can see both the HDMI and Headphone jack in alsamixer but not the internal microphone:

```
    arecord -l
    **** List of CAPTURE Hardware Devices ****
    card 1: Generic [HD-Audio Generic], device 0: ALC257 Analog [ALC257 Analog]
      Subdevices: 1/1
      Subdevice #0: subdevice #0 
```

[IMG]https://i.stack.imgur.com/t6Voa.png[/IMG]

[IMG]https://i.stack.imgur.com/oqTQf.png[/IMG]

The solution in the Arch forum was to add the `snd_pci_acp6x` driver and it's DMIC support in the kernel config. In the inxi output the audio device in question also has the snd_pci_acp6x driver. But I'm not very experienced and not sure whether that applies to Ubuntu or not.

Can someone tell me how to do that in Ubuntu (it's a new system, no problem if it crashes) or has any other idea on how to add the internal microphone to ALSA or to my system?

(I also tried Ubuntu 23.10 with the newest kernel which still doesn't work)

Thank you,
Patrick

---

