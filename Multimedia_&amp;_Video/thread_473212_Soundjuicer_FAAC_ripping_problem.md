---
title: "Soundjuicer FAAC ripping problem"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by sprocket1985 on 2007-06-13
When I rip a cd to m4a files, the playback of the files is intermittent (i.e. a fraction of a second of audio, then silence, then some audio again, etc). Does anyone have any idea what may be happening or how to fix this?
I'm using SoundJuicer and gstreamer-faac

---

### Post by Major_Kong on 2007-06-13
In the AAC profile, what gstreamer pipeline do you use ?

PS: Do you really have to encode to AAC ?

---

### Post by sprocket1985 on 2007-06-14
I'm attempting to rip to m4a for ipod playback. I have limited space, so I'd rather go for m4a than mp3.
Here is my pipeline:

```

audio/x-raw-int,rate=44100,channels=2 ! faac ! ffmux_mp4

```

---

### Post by Major_Kong on 2007-06-18
Try to use more faac encoding options.

Use this:

audio/x-raw-int,rate=44100,channels=2 ! faac profile=1  ! ffmux_mp4

(to edit, use gconf-editor since sound-juicer profile editor is broken. Edit /system/gstreamer/0.10/audio/profiles/aac )

---

### Post by sprocket1985 on 2007-06-18
Thanks, I'll give it a go.
The sound profile editor bug can be worked around. To type into the "Editing profile" window, you have to close the "Edit GNOME Audio Profiles" window.

---

### Post by sprocket1985 on 2007-06-18
Same problem still :(
I've also noticed that the track number tag isn't being written

---

### Post by Major_Kong on 2007-06-19
> **sprocket1985 said:**
> Thanks, I'll give it a go.
The sound profile editor bug can be worked around. To type into the "Editing profile" window, you have to close the "Edit GNOME Audio Profiles" window.

I know, but i find it less annoying to just use gconf-editor.

I guess you can try something else... using gstreamer to encode aac files doesn't appear to be such a good idea (and i suspect the same applies to other formats...), so you can give up and encode to mp3:

```
audio/x-raw-int,rate=44100,channels=2 ! lame quality=0 vbr=4 vbr-quality=5 ! xingmux ! id3v2mux
```

This will give you a ~130 kbps MP3 VBR. But you can change vbr-quality if you think it's too low.

> Portable: background noise and low bitrate requirement, small sizes
vbr=4 vbr-quality=6 (~115 kbps), vbr=4 vbr-quality=5 (~130 kbps) or vbr=4 vbr-quality=4 (~160 kbps) are recommended for this use.
vbr=4 vbr-quality=6 produces an acceptable quality, while vbr=4 vbr-quality=4 should be close to perceptual transparency.

It all depends on your perception.

OR

You can install grip (a cd ripping frontend that doesn't use gstreamer).

OR 

Use command line encoders.

---

### Post by sloggerkhan on 2007-07-15
I recomend grip, I had the same problem you're having with the rhythmbox and sound juicer ripper ONLY when I was ripping to aac / m4a (which I wanted to do to avoid bit loss on a few old DRMed iTunes tracks from a gift certificate I got in middle school). What I think might be happening is that your systems creates some sort of pipe  between CDROM drive and MP4 encoder, or maybe between the Ripped stream from the CDROM and the MP4 encoder, and the ripped stream or cdrom drive is coming in intermentently because it runs at a much slower rate than my system is able to encode @, leaving gaps in the song. When I use grip, which rips the whole track to file, then runs it through the encoder, I have no problems. Only thing I don't like about grip is it doesn't seem to have built in metadata editing.

---

### Post by ibanez88 on 2007-07-25
I'm having the exact same problem.  Should a bug report be filed on this?  

How do I get grip to encode an AAC file?  I see options for .mp3 and .ogg only, with the ability to point to a command line encoder.

---

### Post by sloggerkhan on 2007-07-25
To encode aac in grip, click on the config tab, then the encode sub-tab, and then select faac as the encoder. If you don't have faac you will need to get it from synaptic.

---

### Post by ibanez88 on 2007-07-25
Thanks for the info!  Sorry if I hijacked the thread, although it is relevant to the original post.

---

### Post by sloggerkhan on 2007-07-25
I kinde think the issue might be the pipe between the stream read and the gstreamer-faac encoder which behaves like it's 'listening,' All I know is that I have the same issue, and grip's method of ripping the raw audio and then encoding is what seems to work. I also think the faac grip uses isn't gstreamer-faac, don't know if that's related.

---

### Post by ibanez88 on 2007-07-25
> **sloggerkhan said:**
> I also think the faac grip uses isn't gstreamer-faac, don't know if that's related.

I believe you're right as I hadn't had the package named faac installed until I read the suggestion to use it here.  Interestingly I hadn't even had the gstreamer faac installed that I could tell, unless similar functionality is also present in good/bad/ugly...

---

### Post by sloggerkhan on 2007-07-26
I'm no expert, I might be mixing up names for the gstreamer stuff.

---

### Post by Marcellus on 2007-11-26
I find the same issue with my ubuntu installation (a fresh 7.10).  The suggested solution (editing the profile in SoundJuicer and/or RhythmBox) don't change anything.

Ripped song playback is not so much <intermittent> as <4x longer than usual> --- the song durations are far longer than usual.  Ripping to Ogg is fine, but as with earlier posters, my aim is an iPod so that's no solution.

So, bug report or other solution?

---

### Post by deruberhanyok on 2007-11-26
I had a similar problem. From what I read, sloggerkhan's explanation is about what I'd figured on my own. It's either a bug in the current version of gstreamer-faac (for gstreamer 0.10) or gstreamer-faac simply hasn't been updated (the last mention of it I could find in old documentation for ripping was when gstreamer 0.8 was in use).

The bug is detailed here:

[https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/95326](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/95326)

I also have this problem. I found two solutions: 1) Rip to MP3. 2) If possible, install Rockbox on your iPod (check [The Rockbox website]("http://www.rockbox.org/") to see if your model is supported); this would allow you to rip to OGG as well.

Also I found that rhythmbox, while transferring files to an iPod, was very slow and seemed to be transcoding previously ripped AAC files (for whatever reason, instead of just copying them). The solution there was to just not use Rhythmbox; that bug is also on launchpad, here:

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/164265](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/164265)

For what its worth, you're not alone.

---

### Post by Marcellus on 2007-11-26
Ah, thanks.  Now I see it's low-priority because of licencing/nonfree-ness.  

Using MP3 is not really a choice for me.  I will look into the alternative ripping programs...

M

---

### Post by deruberhanyok on 2007-11-26
I think it's more because the issue hasn't been reported much, but I'm not sure. There's obviously a problem in there somewhere, you'd think someone would want to try and fix it. If I had the programming know-how I'd dive into it myself.

Grip can be configured to use the actual faac program, not the gstreamer plugin, so apparently that works pretty well (it rips then compresses separately). I think abcde works the same way. For now I think the only workaround, if you're specifically trying to rip to AAC, is to use one of those.

Also, anyone else reading this, check out those bugs on launchpad that I linked. Subscribe to the bug page... the more people watching them or contributing info to them, the more interest there may be in getting this one fixed.

---

