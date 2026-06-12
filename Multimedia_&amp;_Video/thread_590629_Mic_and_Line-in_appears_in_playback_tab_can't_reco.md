---
title: "Mic and Line-in appears in playback tab/ can't record"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by Tuxoid on 2007-10-24
In my alsamixer and volume control, Line in, internal mic, and mic appear in the playback tab. They should be appearing in the recording tab. My playback works fine but along with the recording devices being in the wrong tab, out of all my recording devices, only the internal mic works. I am getting ticked-off with because i was planning on doing some screencasts, purchased a headset, only to have the headphone part work like a dream and not being to do the more important thing with my new headset, recording! It's audio-jack based, so, what the heck! I've turned everything on in volume control, everything up, every option for input under the options tab, I have setup my modprobe.d for my audio hardware, tried arecord.](*,)

---

### Post by Tuxoid on 2007-10-25
I am using A RealTek ALC880 sound card. it uses intel hda.

---

### Post by Tuxoid on 2007-10-25
I just lost my audio all together.  I tried to install realtek-linux-audiopack-4.07a. It now thinks I don't have a sound card. I really could use some help. I'm not to with ubuntu configuration yet.

---

### Post by bwhiti on 2008-07-14
I also have the same problem my mic appears in the playback not the recording tab how can I get this working?

---

### Post by Tuxoid on 2008-07-16
Well I found a work-around. I posted it at launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/239597/comments/5]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/239597/comments/5")

Note: This only works if you have an Internal Mic as well a Line-in and a Mic

---

