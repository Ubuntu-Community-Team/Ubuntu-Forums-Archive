---
title: "[SOLVED] bttv: audio works in xawtv, missing in tvtime"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by orzechowskid on 2007-11-24
I have an older STB/Gateway tv card with the bt848 chipset installed on a Gutsy machine.  The tv card's audio output cable is attached to my sound card's CD in.  Both tvtime and xawtv display a picture, but audio only works in xawtv.  tvtime will let me adjust the volume all I want, but I still don't hear any audio.  Playing with the --mixer argument on a command line seemed to have no effect, but I haven't tried every device in /dev plus every channel possible (:aux, :cd, and so forth).

Am I just not using the right command-line arguments for tvtime?  Why does xawtv work without me having to do anything?  Is there something else I'm overlooking?

Thanks in advance for any help.

---

### Post by orzechowskid on 2007-11-24
bump with additional information:

if I run gnomeradio, it appears to mute and un-mute the tv card's internal mixer properly like xawtv does.  The card's mixer gets set to full volume, and gnomeradio's volume slider controls the appropriate ALSA mixer channel.  When xawtv is running, its volume control seems to affect the tvcard mixer's volume directly.

So I guess my questions now are, how can I get tvtime to un-mute the card's mixer on startup, and mute it again when I'm done watching tv?  Can I get gnomeradio to set my card's mixer volume to anything but full blast?  Can I get tvtime to do anything to it at all?

thanks!

---

### Post by orzechowskid on 2007-11-27
one more bump:

it appears that tvtime thinks my card is a v4l2 device, when that doesn't seem to be the case.  I'll have to figure out what's going on later, but for now commenting out the v4l2-specific code in the source and recompiling did the trick for me.

---

