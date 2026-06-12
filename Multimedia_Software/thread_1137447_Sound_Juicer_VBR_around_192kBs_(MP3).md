---
title: "Sound Juicer: VBR around 192kB/s (MP3)?"
date: 2009-04-25
forum: Multimedia Software
---

### Post by keenPenguin on 2009-04-25
Hi, 

I would like to rip tracks of an audio CD into MP3 files. As far as I've read variable bitrates seem to be recommended, while constant bitrates are not. I would like a bitrate around 192kB/s, and possibly above, as I sometimes feel that something about 160kB/s are not sufficient. So I wanted to configure a ripper to rip with a VBR and around 192kB/s. I tried the standard ripping tool on my Ubuntu 8.04, Sound Juicer, and got a little confused.

I created a profile, but I wonder what to write in the GStreamer pipeline field? I googled and found a [German Wiki site]("http://wiki.ubuntuusers.de/Sound_Juicer"), which suggests this:

**192 kbps constant bitrate**

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1 quality=0 vbr=0 bitrate=192 ! xingmux ! id3v2mux
```

** VBR ~190kbps**

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1 quality=0 vbr=4 vbr-quality=2 ! xingmux ! id3v2mux
```


I tried both and found that the VBR line is quite fast at ripping, but yields bitrates which are below 160kB/s (the CD I tried was an audiobook), which is not sufficient. The constant one does manage 192kB/s, but it's awfully slow in ripping (requires twice or thrice the time for as the VBR one). 

I also found that there are some other ways, like presets (standard, ..., extreme) and tried this line which I found somewhere (I haven't bookmarked it):

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=extreme ! xingmux ! id3v2mux
```

The bitrates I got from this are pretty much the same as with the ~192kB/s VBR one. They're below 160. 

Perhaps that's because the codec believes that by raising the bitrate it would hardly get any quality, so it's more efficient to stay with the lower bitrate? 

Is there a way to use a VBR method, but increase its mean bitrate? so that my audiobook CD would be ripped with more than about 160kB/s?

Also, [this wikipage]("https://help.ubuntu.com/community/CDRipping#Sound%20Juicer") says that Sound Juicer (or rather the GStreamer pipeline stuff) totally sucks and should be replaced by some other ripper. Yet the German wikipage I linked above says no such things and claims that it has been tested with my beloved Hardy. Who's right? Is there something wrong with Sound Juicer?

I'd be grateful if you shed some light in this; maybe all I need is just a line for the GStreamer pipeline filed, and maybe a different ripper (which?).

---

### Post by logos34 on 2009-04-25
yeah, neither preset=standard, preset=1001 or any of the vbr gstreamer lines appear to work anymore.  Your line 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1 quality=0 vbr=4 vbr-quality=2 ! xingmux ! id3v2mux

is exactly what I had mine set for (did it a few releases back), and recently I went to use it and found it was outputting ~160kbps (wtf?).  Unless the tags are wrong.

I have never liked sound juicer, nor ever used it much...poorly designed and needlessly complicated, IMO...I wouldn't even have it on my machine except to troubleshoot...

My advice: use Exact Audio Copy (wine), or any of the excellent [rippers here]("https://help.ubuntu.com/community/CDRipping#Other%20CD%20Ripping%20Software"). (abcde is probably my fav...Rubyripper is great if you need an absolutely secure rip like EAC produces)

---

### Post by keenPenguin on 2009-04-30
Hi logos34, 

thank you! It's good to know that I'm not all wrong. Anyway, I tried different rippers and found that I prefer Grip. It rips fine and fast with a constant 192kB/s bitrate (or whatever I choose).

---

### Post by logos34 on 2009-04-30
> **keenPenguin said:**
> Anyway, I tried different rippers and found that I prefer Grip. 

yep, grip used to be my fav.  

enjoy!

---

