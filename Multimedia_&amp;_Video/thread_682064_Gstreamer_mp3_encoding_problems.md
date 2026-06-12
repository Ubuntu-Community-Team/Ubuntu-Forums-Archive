---
title: "Gstreamer mp3 encoding problems"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by timothy.malone on 2008-01-29
So, using standard mp3 encoding settings with Sound Juicer and rythmbox works fine. That is full stereo and constant bitrate of 128. When I change the pipeline to use lame standard presets, the mp3 it spits out at me is all choppy when played back. If I use Grip instead which doesn't use gstreamer and choose the same preset, everything is fine. Anybody know why? Also, why is it so difficult to make good pipelines in gstreamer. There must be a better way. At least include a few more pipelines so people don't have to edit them.

---

### Post by disturbed1 on 2008-01-29
What's the pipeline your using?

Did you look at gst-inspect-0.10 lame to make sure you passed the correct settings. In lame (cli) if you want a quality of 0, you simply use -q 0, for gst it's quality=0. If you want simple stereo it's -m s for gst it's mode=0. As you can see they aren't the same.

---

### Post by timothy.malone on 2008-01-29
the only options I'm passing are "standard=1001".
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc quality=0 preset=1001 ! xingmux ! id3v2mux
when I just use lame on the command line with --preset standard (the equivelent of 1001), it works fine. It also works fine with grip. In fact, I can't get gstreamer to make a good mp3 with any other settings than the ones that were installed by default. Every other option gives me the same choppy sound. I've also tried without xingmux and without the quality setting. Are the presets within gstreamer somehow different than the ones for standard lame?

---

### Post by disturbed1 on 2008-01-29
Take out either ! xingmux or ! id3v2mux (! xingmux is really only usefull for writing the xing vbr header instead of the lame tag)
Try standard, or Standard instead of 1001. Using quality=0 is different than using the standard preset as well.

You could try this

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc quality=0 bitrate=192 ! id3v2mux

---

### Post by timothy.malone on 2008-01-29
Thanks for the reply.
I've tried all that, every combination I can think of with gstreamer. Nothing changes the results (I can't even get back to what was working previously). The sound isn't just choppy though, it's as if the sound is slightly out of order, or maybe that the channels were encoded in a funky way. Switching to mode=0 doesn't help though. Lame itself works perfectly.

---

### Post by disturbed1 on 2008-01-29
That is quite strange. What repo did you install the GStreamer-lame plugin. If it wasn't the official Ubuntu repo, this could the issue.

Here's my pipeline for soundjuicer, which I just now did check to make sure it works.
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 quality=0  bitrate=192 ! id3v2mux


Runing gst-inspect-0.10 lame gives me this (and quite a bit more ;) )
> 
Factory Details:
  Long name:    L.A.M.E. mp3 encoder
  Class:        Codec/Encoder/Audio
  Description:  High-quality free MP3 encoder
  Author(s):    Erik Walthinsen <omega@cse.ogi.edu>, Wim Taymans <wim@fluendo.com>
  Rank:         none (0)

Plugin Details:
  Name:                 lame
  Description:          Encode MP3s with LAME
  Filename:             /usr/lib/gstreamer-0.10/libgstlame.so
  Version:              0.10.6
  License:              LGPL
  Source module:        gst-plugins-ugly
  Binary package:       GStreamer Ugly Multiverse Plugins (Ubuntu)
  Origin URL:           [https://launchpad.net/distros/ubuntu/+source/gst-plugins-ugly-multiverse0.10](https://launchpad.net/distros/ubuntu/+source/gst-plugins-ugly-multiverse0.10)


---

### Post by timothy.malone on 2008-01-29
more testing reveals that something is just messed up with my gstreamer install. None of the encoders work correctly. Playback is fine. I'm actually wondering if the problem isn't with the encoders but with the ripping portion. The process of ripping and encoding in gstreamer apps is a lot faster than with grip. I do have an old cd drive.

---

### Post by disturbed1 on 2008-01-29
SoundJuicer doesn't use cdparanoia by default, but I believe Grip does.

A quick test would be to rip a single song with SoundJuicer to wav or FLAC format and play it back, if that's screwy, it could be either a GSTreamer fault, or the CD/CD Drive isn't jiving with SoundJuicer. If in doubt you could always mark the GSTreamer apps/codec for reinstall through synaptic.


audio/x-raw-int,rate=44100,channels=2 ! wavenc name=enc



I'd highly reccomend RubyRipper, but only if you want accurate rips, it isn't for speed. As it rips each track twice to do a compare to make sure it's 100% correct without errors. [http://code.google.com/p/rubyripper/downloads/list](http://code.google.com/p/rubyripper/downloads/list)

---

### Post by timothy.malone on 2008-01-29
well, I ripped a track with cdparanoia and then encoded it with gstreamer. It worked fine. So now I will investigate how to change the gstreamer ripping settings. Thanks again.

---

### Post by disturbed1 on 2008-01-29
> 
1. start the terminal and type: **gconf-editor**
2. goto: **apps/sound-juicer**
3. look at the paranoia key. it should say 16. Change it to **255** to enable full paranoia.
4. close the configuration editor (you can always change it back if you want to).

^^Credit to [mekkah](http://ubuntuforums.org/member.php?u=129519)

---

### Post by timothy.malone on 2008-01-29
I also tried ripping with sound-juicer and the resulting file was fine. So, it seems to me that something goes wrong when gstreamer tries to do everything together. Which is sorta what the sound file I get out of the process sounds like. It plays for a second then sounds like it jumps back, then goes back to where it was for a second then jumps around some more. Maybe gstreamer is assembling the frames in the wrong order.

---

