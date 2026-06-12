---
title: "Dual Monitors on Linux - GeForce 6200 AGP 8X"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by -falco- on 2006-09-16
I just bought a New graphics card for my compie - Geforce 6200 128MB 64-bit DDR AGP 4X/8X Video Card. I was wondering how I could run dual monitors, because there is 2 monitor ports in the card. I am a linux n00b so I need step by step instructions :D. Also, it comes with a port for hooking up a TV to it, and I was wondering if thats worth it or not?

---

### Post by tronica on 2006-10-27
pretty easy to get going, first install the nvidia driver, follow this

> sudo apt-get install nvidia-glx nvidia-kernel-common

then we need to edit your xorg.conf

> sudo gedit /etc/X11/xorg.conf

then comment out DRI like so

> #       Load    "dri"
    

then go down to the device section and change the driver to "nvidia"

now add 
> Option          "twinview"


it should look something like this

> Section "Device"
        Identifier      "NVIDIA GeForce 6600"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
        Option          "twinview"

now save and restart X by doing Ctrl+ALT+backspace

also this topic should be moved i think

---

