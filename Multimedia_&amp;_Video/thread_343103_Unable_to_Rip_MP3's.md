---
title: "Unable to Rip MP3's"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2007-01-20
I am using Sound Juicer to rip a CD to MP3. I read the manual which states I need to create a new profile called "mp3" and then add the following in GStreamer Pipeline:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux
```

I enabled this profile and then restarted Sound Juicer but when I try and rip MP3's, it locks up. I downloaded also the following .deb package from APT

```
gstreamer0.8-lame - LAME encoder plugin for GStreamer

```

Anyone know what I am doing wrong?

---

### Post by ajm2005 on 2007-01-21
> **Carlwill said:**
> I am using Sound Juicer to rip a CD to MP3. I read the manual which states I need to create a new profile called "mp3" and then add the following in GStreamer Pipeline:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux
```

I enabled this profile and then restarted Sound Juicer but when I try and rip MP3's, it locks up. I downloaded also the following .deb package from APT

```
gstreamer0.8-lame - LAME encoder plugin for GStreamer

```

Anyone know what I am doing wrong?


would you need to have lame installed, or does the gstreamer lame plugin take care of that?

out of interest, are you able to get the music off the CD in "wav" format? at least that would be a first step. I suppose you could then use SoundKonvertor to compress the wav files down to mp3.

sorry if this wasn't much help, but at least it will bump the post :)

---

### Post by navneeth on 2007-01-23
Bumping!

I'm having the same problems, too.

---

### Post by compwiz18 on 2007-01-23
I'm pretty sure all you need to do is open sound-juicer, create new profile (named mp3), edit that profile, enter "lame" as the gstreamer pipeline, and mp3 as the file extension.  This will get you 128kbps mp3s.  Anything else, and you're on your own :P I'll try and help though.

Make sure you have lame installed, and you may need to restart Sound Juicer once you have created the profile.

---

### Post by navneeth on 2007-01-23
> **compwiz18 said:**
> I'm pretty sure all you need to do is open sound-juicer, create new profile (named mp3), edit that profile, **enter "lame" as the gstreamer pipeline**, and mp3 as the file extension.  This will get you 128kbps mp3s. 

That did the trick. Thanks.

Btw, what should I do to get a higher bit rate?

---

### Post by hakan69 on 2007-01-23
Hi
I' using this line in gstreamer and it works OK. I installed soundcodecs wiht Automatix 
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux
Regards/Hakan

---

### Post by chrisby on 2007-01-25
yea, the problem is that they have the bit rate set to 196 instead of 192.  I also found that sound juicer freezes when I want to rip single tracks, but not at all with the whole cd.

---

