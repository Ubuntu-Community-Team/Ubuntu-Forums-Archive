---
title: "Please help with Totem-Xine + DVD (Different problem)."
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by volanin on 2007-04-22
Ok, I have the following problem:

I put a DVD in the drive, fire up TOTEM-XINE, and click:
Movie -> Play Disc "DVD NAME"

But, instead of playing the DVD, totem shows me the FILE SELECTION dialog.

I can choose a VOB file, and it will play fine, even if it is encrypted,
but the full DVD just won't play normally like it should on a DVD player.
The file selection dialog always shows up, showing me the folders AUDIO_TS and VIDEO_TS.

Also, I cannot play the ISO IMAGES of my DVDs.
It says 'No plugin to handle this movie'.
This didn't happen in Edgy...

MPlayer and Xine-ui all play the DVD just fine.
But I would like to make it work in TOTEM-XINE, as it's my default player for everything.

I already have these packages installed:
[LIST]
[*]totem-xine
[*]libxine1
[*]libxine-ffmpeg
[*]libxine-extracodecs
[*]libdvdread3
[*]libdvdplay0
[*]libdvdnav4
[*]libdvdcss2
[/LIST]

Does anyone else has this behaviour?
(By the way, I already tried purging all these packages and reinstalling again.)

---

### Post by rumli on 2007-04-23
Same problem here.  I get the following error: "There is no plugin to handle this movie."

It worked fine on Edgy.

Edit:  I should clarify by saying that I can play actual DVDs but I can't play ISOs.

---

### Post by p_schott on 2007-04-24
Same problem for me since I upgraded to feisty.

---

### Post by ubu-for on 2007-04-24
> **volanin said:**
> Does anyone else has this behaviour?

DVDs don't work with Totem-Gstreamer but with Totem-Xine.

---

### Post by ubu-for on 2007-04-24
> **volanin said:**
> Also, I cannot play the ISO IMAGES of my DVDs.
It says 'No plugin to handle this movie'.

Same here with Totem-Gstreamer! But ISOs work with VLC and MPlayer.

---

### Post by rumli on 2007-04-26
I found out how to play an ISO with totem-xine:

```
totem dvd://absolute/path/to/dvd.iso
```

I then used Nautilus Actions (search for "nautilus-actions" in Synaptic) to add a right-click action to play ISOs in Totem directly from the Nautilus file browser without having to go to the command line.

---

### Post by aidanr on 2007-05-15
thanks rumli, just came across this and that was a quick and easy fix, added a custom action in thunar :)

---

