---
title: "Sound crashed"
date: 2011-04-07
forum: Multimedia Software
---

### Post by donpeter06 on 2011-04-07
Hi i am using ubuntu 10.10.
Its been quite a while now.
Everything was fine. But now today when i tried to  play a movie file in vlc there is no sound(both in headphone and in speakers).


Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device 8290
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at dfff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

I tried to reinstall my VLC but in vain.
Please Help.


My alsa report is here.
[http://www.alsa-project.org/db/?f=c44a9ca1450251a0d01988a07ca733c51be41256](http://www.alsa-project.org/db/?f=c44a9ca1450251a0d01988a07ca733c51be41256)

---

### Post by lidex on 2011-04-10
Any idea what precipitated this? It's not going to go out for no reason. A recent update/upgrade? Your alsa-info looks fine.

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=asus-mode3" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Yellow Pasque on 2011-04-10
It could be the old .pulse corruption..
```
rm -rf ~/.pulse*
pulseaudio --kill
```

---

### Post by lidex on 2011-04-10
You'll also want to try other media players and if they work check the audio output in vlc > tools > preferences > audio.

---

### Post by donpeter06 on 2011-09-11
Sorry for the laaate reply.
I had installed some kind of sound tuner.
I just uninstalled it and everything is pretty fine now.
thanx

---

