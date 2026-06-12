---
title: "changing sound cards"
date: 2011-02-27
forum: Multimedia Software
---

### Post by coze on 2011-02-27
hello there,
I'm using lubuntu 10.10, fresh install.
I got a PCI sound card, midiman audio, which works perfectly fine with the ice1712 mod.
recently I purchased a ATI Saphire graphics card, which also also HDMI output.
I did a fresh install of lubuntu 10.10. The default sound output was recognised as HDMI sound. I wanted to use the m-audio card, so I blacklisted  snd-hda-intel.
Now the sound works fine out my m-audio card. but when I start to play a file with mplayer I get a message 

Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

so it seems to be looking for something thats not there.
The sound works fine despite this message.
I would like to know how can I prevent mplayer looking for this nvidia driver ?
thanks :popcorn:

---

### Post by Yellow Pasque on 2011-02-27
It's a harmless warning message. Install libvdpau if you don't want to see it.

---

