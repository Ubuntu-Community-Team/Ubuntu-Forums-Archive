---
title: "Firefox sound locked to SPDIF output"
date: 2013-03-26
forum: Multimedia Software
---

### Post by bnilsson on 2013-03-26
Ubuntu Studio 12.04LTS
Gigabyte 880GA-UD3H
snd_hda_intel

My Firefox sound (flash?) output has somehow become locked to my mobo SPDIF output. I prefer it to go via the HDMI. It seems not to be connected to the "default sound card" issue, since if I disable onboard sound (Analog +Digital)  in BIOS I still don't get anything on the HDMI anyway. Other applications such as Audacious works fine over the HDMI.

What could have happened? How do I release it?

---

### Post by bnilsson on 2013-03-29
Ok, I gave up and reinstalled 12.04 from scratch on a new SSD disk.
Now the HDMI output is working again.

---

### Post by zika on 2013-03-29
> **bnilsson said:**
> Ubuntu Studio 12.04LTS
Gigabyte 880GA-UD3H
snd_hda_intel

My Firefox sound (flash?) output has somehow become locked to my mobo SPDIF output. I prefer it to go via the HDMI. It seems not to be connected to the "default sound card" issue, since if I disable onboard sound (Analog +Digital)  in BIOS I still don't get anything on the HDMI anyway. Other applications such as Audacious works fine over the HDMI.

What could have happened? How do I release it?Did You try ```
gstreamer-properties
```?

---

### Post by bnilsson on 2013-03-29
No, I did not. I might have if you had suggested it yesterday:).
Now it's history.

---

### Post by zika on 2013-03-29
> **bnilsson said:**
> No, I did not. I might have if you had suggested it yesterday:).
Now it's history.I wrote my answer to give You a hint for resolution of a possible problem next time...

---

### Post by bnilsson on 2013-03-29
Ok, on your advice I installed gnome-media, and I found this set of utilities gives me much better control and understanding of the media flow.
Especially streamer-properties.
Thanks a lot!:)

---

### Post by bnilsson on 2013-04-05
Just got the same problem back, by making the mistake of manually installing the latest version of alsa into the recently reinstalled Ubuntu Studio 12.04LTS.

The reason was that I had a new go on trying to get my EMU1212m PCIe sound card working, following the instructions in [http://askubuntu.com/questions/264919/how-to-get-emu-1212m-emu-1616m-or-emu-1010-to-work-with-ubuntu-12-10](http://askubuntu.com/questions/264919/how-to-get-emu-1212m-emu-1616m-or-emu-1010-to-work-with-ubuntu-12-10).

I did not make the connection at first, but I now realize that I did the same operation just before my Firefox flash sound output got stuck to SPDIF the first time, that was the cause I opened this thread in the first place. 

The procedure did not make my EMU1212 work then, and not this time either. And I lost my Firefox HDMI sound in the process. Again.

I will try the gstreamer-properties to get it back but I seriously doubt it will help me, I think this runs deeper.

However, the procedure described in the link above may not be wrong as such , but the result for me just proves that building and installing the latest version of ANYTHING involves a risk.

---

### Post by bnilsson on 2013-04-06
And, as I come to think of it, the new alsa install also caused my Cambridge DACMagic USB DA-converter to be unrecognized as an audio device.

---

### Post by kostkon on 2013-04-06
You need to install the PulseAudio Volume Control utility (pavucontrol package), start a flash video in Firefox and then send the audio from flash to the device you want using pavucontrol.


Hope that helps.

---

### Post by bnilsson on 2013-04-06
Did that as the first thing, had no effect.

---

