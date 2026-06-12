---
title: "Help fixing my audio recording gnome-shell"
date: 2012-07-06
forum: Multimedia Software
---

### Post by CostaMichailidis on 2012-07-06
Hi!

I've been trying to fix a problem for a couple of months now, any help would be tremendously appreciated!

I'm running ubuntu 11.10 with a Gnome shell. There is a keyboard shortcut I really liked, ```
ctrl + alt + shift + r
``` starts recording your screen and then hitting that key combo again stops recording and the screencast is saved to my home folder, awesome! I noticed this wasn't recording audio, got a little greedy and tried to figure out how to add audio recording to the mix. I took someone's advice on ask ubuntu and pasted this into my terminal:

```
gsettings set org.gnome.shell.recorder pipeline "queue ! videorate !  vp8enc quality=10 speed=2 ! mux. pulsesrc ! audio/x-raw-int ! queue !  audioconvert ! vorbisenc ! mux. webmmux name=mux"
```I tested out my new configuration and bam, audio was being recorded! Except it never stopped recording, where screen recording ended, audio recording continued until I deleted the file or logged out or restarted.

It would be awesome to put things back to normal, it would be hella awesome to be able to stop recording audio upon hitting the key combo the second time.

If you can help you are my hero!

---

