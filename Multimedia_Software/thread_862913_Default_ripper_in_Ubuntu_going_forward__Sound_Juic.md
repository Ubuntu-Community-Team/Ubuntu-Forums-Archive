---
title: "Default ripper in Ubuntu going forward?  Sound Juicer needs some simple improvements."
date: 2008-07-18
forum: Multimedia Software
---

### Post by thedevnull on 2008-07-18
Is Sound Juicer going to be the default CD ripper in Ubuntu going forward?  It isn't documented and doesn't seem to have any normal way to set the bitrate and other core settings.  Its not really Ubuntu user friendly....

See what others say...

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)
[http://ubuntuforums.org/showthread.php?t=346897](http://ubuntuforums.org/showthread.php?t=346897)

Arguably a regular user isn't going to want to put this into the settings:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 vbr-min-bitrate=160 vbr-max-bitrate=192 ! xingmux ! id3v2mux

I am would certainly be willing to talk to the developer but I wanted to know if that is what we are sticking with.

For those wondering why I am still buying CD's its cuz I HATE DRM!  

Thanks and have a great weekend,
:guitar:

---

### Post by bsmith1051 on 2008-07-26
I Second...

---

### Post by cariboo on 2008-07-26
I think the idea is that a regular user isn't going to bother with fine tuning the settings so they have been set at average values. For those of use who want better quality, we are going to find something that suits us better. My personal favourite ripper is **grip** you can set it up any way you want from whatever bitrate to what encoder you want to use. To me that is the idea behind Ubuntu, use it until you are comfortable with it, then customize it to whatever floats your boat.

Jim

---

### Post by Yellow Pasque on 2008-07-26
Instead of vbr mp3, consider ogg/vorbis if your media players support it, or better yet, FLAC, since disk storage is pretty cheap these days.

---

### Post by bsmith1051 on 2008-07-27
Talk of OGG or FLAC is totally irrelevant to Joe Six-Pack.  And my concerns re Sound Juicer have nothing to do with the 'command-line' fine tuning and everything to do with the fact that MP3 support is SO HARD TO MAKE WORK.  Everytime I think I have it working it gets broken by something, e.g. updates.  Currently, my copy is NOT WORKING and I have no idea why.  I have read and re-read all the posts (itself a bad sign) suggesting ways to make MP3 recording work.

It's ridiculous that I should ever have to fix the MP3 support...

---

### Post by Yellow Pasque on 2008-07-27
Well, Ubuntu is **F**ree, **O**pen **S**ource **S**oftware. Talk of free, open source formats is not irrelevant.

---

### Post by Major_Kong on 2008-07-27
Well, soundjuicer just tries to be "good enough"...

Personally, i prefer Rubyripper. It uses secure audio ripping and doesn't rely on gstreamer for encoding. A better choice overall.

---

### Post by vanadium on 2008-08-02
I am not anymore sure of the "secure" part of rubyripper.

* I had a gapless rip where there was a serious click between two tracks (playing back "gaplessly with mpd). Appeared - in Audacity - that the end of the previous track overlapped a (tiny) bit with the next.
* I had a track that was ripped successfully "with correction" after 23 trials. Obviously, some artifacts showed up. If yur CD drive reproduces the same errors three times out of 25 times, the file is reported to be successfully ripped. It is a track where Exact Audio Copy even with the highest correction setting does not succeed without error. There is a ripper where you are sure if the report says "succes".

We do not have secure ripping on Linux.

---

### Post by bsmith1051 on 2008-08-02
FYI - 'grip' doesn't seem to be including the MP3 ID2/ID3 tags.

---

### Post by shirilover on 2008-08-02
I assume you have looked at the ID3 config tab?
Another possibility is to add the following to the lame command line
```

-V 0 --add-id3v2 --pad-id3v2 --ta "%a" --tt "%n" --tl "%d" --ty "%y" --tn "%t" %w %m

```

---

### Post by bsmith1051 on 2008-08-03
> **shirilover said:**
> I assume you have looked at the ID3 config tab?
Good god, it was defaulted to 'off'.  I'd checked the settings but hadn't read the exact wording on that part because I assumed the default was 'on'.

Thanks!

---

