---
title: "Amarok will not play Ogg Vorbis or MP3 after reinstalling Feisty"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by Greg K Nicholson on 2007-06-15
I had an install of Ubuntu Feisty in which Amarok was able to play Ogg Vorbis and MP3 audio; but after reinstalling Feisty (I have a separate /home partition) Amarok will no longer play either Ogg Vorbis or MP3 audio.

Amarok shows the message "No suitable demux plugin. This often means that the file format is not supported." when trying to play anything. Installing libxine-extracodecs seems to instead make Amarok pop up a dialogue saying something like "MP3 support not installed" with an option to install it. However as soon as the dialogue appears, Amarok freezes *before* I can click the button; this is [Launchpad bug 58617](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/58617). Contrary to the workaround mentioned in [comment 22 of that bug](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/58617/comments/22), installing libxine-extracodecs manually doesn't solve the problem (in fact it seems to be *exposing* the problem).

The xine-check command says (in the first person), "I have found multiple xine executables on your machine: /usr/bin/xine & /usr/X11R6/bin/xine"; that there are no input, demux, decoder, video_out, or audio_out plugins and that I "should probably reinstall xine-lib...". However, there is no package called xine-lib (I have universe and multiverse enabled).

I currently have **amarok-xine**, **libxine1**, **libxine1-ffmpeg** and **libxine-extracodecs** installed. **Which other packages do I need to install to make Amarok play Ogg Vorbis and MP3 audio?**

More generally, why doesn't Amarok specify all of its dependencies properly? (And is there a bug number for this?) As another example, it complains that khelpcenter is not available when trying to launch the Help documentation.

---

### Post by Greg K Nicholson on 2007-06-21
Uninstalling and reinstalling **libxine-extracodecs** seemed to fix this, although I'm not entirely certain that that's what did it.

---

