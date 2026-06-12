---
title: "multible audio channels for a video file?"
date: 2009-10-16
forum: Multimedia Software
---

### Post by Arminius on 2009-10-16
is there a video format that supports multible audio?
for example when I back my dvd's up to my media servor, thus far I can only do one audio, and leave the commentary's on the dvd's.

Is it possible to have more then 1?

---

### Post by andrew.46 on 2009-10-18
Hi Arminius,

I believe the *best* container format for multiple audio channels is the Matroska container. This is best used under ubuntu with mkvtoolnix:

```
**[COLOR="Red"]mkvtoolnix[/COLOR]** - Set of command-line tools to work with Matroska files
**[COLOR="Red"]mkvtoolnix-gui[/COLOR]** - Set of tools to work with Matroska files - GUI frontend
```

All the best,

Andrew

---

### Post by Arminius on 2009-10-19
can it be used as a dvd ripper?

---

### Post by Arminius on 2009-10-19
doesn't appear to be able to
keeps saying "Reading encrypted VOBs is not supported."

---

### Post by surfed on 2009-10-19
> **Arminius said:**
> doesn't appear to be able to
keeps saying "Reading encrypted VOBs is not supported."

You are looking for "HANDBRAKE", google it.

---

### Post by Arminius on 2009-10-19
yeah handbrake looks like it can do all I want.

just having trouble getting "movie player" to play the final product
tried different formats and mp3 and aac.

none are working so far, what settings is everyone else using? and what media player?

also, I'm going to be using mediatomb to watch these over the ps3, so anyone knows if ps3 can play .ogm or .mkv or .mp4?

---

### Post by surfed on 2009-10-19
Handbrake has presets for ps3 ipods and such.
For Movie Player to play those files you will need the restriceded codecs installed, search the forums or wiki there is lots of info on the subject.

---

### Post by Arminius on 2009-10-19
presets? not seeing where those are.

was using .mkv vorbis, but it only plays 1 audio, then when u go to the next audio dies, and can't even go back to the first one which was working.

---

### Post by Arminius on 2009-10-19
oh and I have all the medibuntu stuff installed.
I assume that's what u ment by restricted codecs?

---

### Post by surfed on 2009-10-19
Presets are in View --> presets
Audio: you have to add the Tracks you like with the plus sign in the audio tab

---

### Post by Arminius on 2009-10-19
the only thing under view is show activity, show preview and show queue.

I know how to add the audios, but in the output file only the first one will play right, when u switch over audio dies.

---

### Post by surfed on 2009-10-19
What version of Handbrake are u you running? I am using svn2845.

---

### Post by surfed on 2009-10-19
check:
[http://trac.handbrake.fr/wiki/Presets](http://trac.handbrake.fr/wiki/Presets)

---

### Post by surfed on 2009-10-19
And I just found this on their site:
* AVI: AVI is a rough beast. It is obsolete. It does not support modern container features like chapters, muxed-in subtitles, variable framerate video, or out of order frame display. Furthermore, HandBrake's AVI muxer is vanilla AVI 1.0 that doesn't even support large files. The code has not been actively maintained since 2005. Keeping it in the library while implementing new features means a very convoluted data pipeline, full of conditionals that make the code more difficult to read/maintain, and make output harder to predict. As such, it is now gone. It is not coming back, and good riddance.

* OGG/OGM: HandBrake's OGM muxer is just as out of date. It hasn't been actively maintained in years either, and it too lacks support for HandBrake's best features. It requires conditionals to work around missing functionality too...only this one gets tested so infrequently the conditionals were never even put in the code, so it just fails when you try to do anything advanced. This one is not coming back either. And yes, we're aware of HTML 5. For patent-free muxing, HandBrake still has Matroska.

* XviD: HandBrake, these days, is almost entirely about H.264 video, aka MPEG-4 Part 10. This makes it rather...superfluous to include two different encoders for an older codec, MPEG-4 Part 2. When choosing between FFmpeg's and XviD's, it came down to a matter of necessity. We need to include libavcodec (FFmpeg) for a bunch of other parts of its API, like decoding. Meanwhile, XviD's build system causes constant grief (it's the most common support query we get about compiling, after x264's requirement of yasm). Since we mainly use MPEG-4 Part 2 for testing/debugging, and recommend only H.264 for high quality encodes, Xvid's undisputed quality edge over FFmpeg's encoder is inconsequential, while FFmpeg's speed edge over XviD is important to us.

* Video game presets: There are no more presets for the PSP, PS3, or Xbox 360. Quite frankly, they didn't work well. None of the development team members own the devices, so testing was minimal and support was nonexistent. Keeping up with the firmware vagaries and ambiguous specifications of these devices was not fun -- we get enough of that from Apple's kit, and those we all have around to test on. The new "Normal" preset should work perfectly fine on any device that supports standard Main Profile H.264 with AAC-LC audio in an MP4 file, which the PS3 and 360 ostensibly do.

HandBrake
     
    Posts: 21
    Joined: Fri Jul 25, 2008 11:40 pm

---

### Post by Arminius on 2009-10-19
version number just says HandBrake 0.9.3

got it from [http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)
and got it today

I'll read that post.

was just hoping u might have done exactly what I'm trying to do :)

---

