---
title: "No sound after 18.04 fresh install"
date: 2019-04-26
forum: Multimedia Software
---

### Post by r102 on 2019-04-26
I just installed Xubuntu 18.04 LTS for the first time on my new laptop, but there is no sound. I checked, pulseaudio is installed. I am dual boot-ing, and on Windows 10 there is sound, so the problem is software not hardware. If I connect wired speakers there is no sound either. Also, the sound icon from top right is greyed out.

The output for sudo lshw -C multimedia is: 

```
  *-usb:2                   
       description: Video
       product: HP HD Webcam [Fixed]
       vendor: DCQFE02BI4S8Y1
       physical id: 3
       bus info: usb@1:1.3
       version: 22.11
       capabilities: usb-2.00
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
  *-multimedia
       description: Audio device
       product: 7 Series/C216 Chipset Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:34 memory:d4730000-d4733fff


```

---

### Post by kryten35 on 2019-04-27
Try these 3 commands one after another.

```
sudo apt remove alsa-base pulseaudio

sudo apt install alsa-base pulseaudio

sudo alsa force-reload
```

Then check in alsamixer that nothing that you need is muted. MM=muted, 00=Unmuted.

```
alsamixer
```

---

