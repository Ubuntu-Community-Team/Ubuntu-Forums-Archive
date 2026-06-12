---
title: "No sound device in Sound Preference"
date: 2010-08-28
forum: Multimedia Software
---

### Post by zmp on 2010-08-28
Hey everyone,

Ive been trying to figure out how to make input work on my sound card device and followed a bunch of guides, which in the end screwed up everything and now i cant seem to find my sound card in Sound Preference. Tried searching on the forums for anything, like reinstall alsa, pulseaudio etc.

alsaconf and lshw seems to be able to detect my sound card.

sudo lshw:
> 
           *-multimedia
                description: Multimedia audio controller
                product: SB X-Fi
                vendor: Creative Labs
                physical id: 7
                bus info: pci@0000:03:07.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=SB-XFi latency=32 maxlatency=5 mingnt=4
                resources: irq:17 ioport:ac00(size=32) memory:efc00000-efdfffff memory:e8000000-ebffffff


I just dont understand why its not in Sound Preference in Ubuntu anymore. - [http://imageshack.dk/imagesfree/ihL98536.png](http://imageshack.dk/imagesfree/ihL98536.png)

Any help is appreciated.

Thanks :)

---

### Post by jmfal on 2010-08-28
Welcome to ubuntu

open a terminal: applications>qccessories>terminal

      ```
 alsamixer
```

Make sure master,pcm, mic/line in are turned up >use l/r arrows on keypad to change selection up/down arrows to raise/lower, sometimes not all sliders are visible in terminal screen, press rt/arrow to bring into view.

make sure correct sound card is selected, press F6 to see options, 

What app are you using, make sure correct card is selected ?

---

### Post by lidex on 2010-08-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by zmp on 2010-08-28
Thanks for the responses :)

Heres the link from using the alsa info script: [http://www.alsa-project.org/db/?f=1e3ac28b551c245894282df5a4777745092e69d0](http://www.alsa-project.org/db/?f=1e3ac28b551c245894282df5a4777745092e69d0)

---

### Post by lidex on 2010-08-28
> **zmp said:**
> Thanks for the responses :)

Heres the link from using the alsa info script: [http://www.alsa-project.org/db/?f=1e3ac28b551c245894282df5a4777745092e69d0](http://www.alsa-project.org/db/?f=1e3ac28b551c245894282df5a4777745092e69d0)

You have a mismatch in alsa components.If you have alsa-backports installed, please uninstall, then use the upgrade link in my sig to get v 1.0.23

---

### Post by zmp on 2010-08-28
> **lidex said:**
> use the upgrade link in my sig to get v 1.0.23

Thanks, that worked. Now i can see my card and play sound again.

Thanks again :)

---

### Post by lidex on 2010-08-28
You're welcome!

---

