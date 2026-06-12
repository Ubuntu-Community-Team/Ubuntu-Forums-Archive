---
title: "Totem/VCL failing on many video formats"
date: 2008-11-29
forum: Multimedia Software
---

### Post by wheezer on 2008-11-29
Ever since I went to Hardy, both Totem and VCL fail on many downloaded DVDs. The downloads work fine in windows.
 
I have spent ours trying to reinstall things, install restricted extras, etc. Nothing works.
Some videos with DivX MPEG5 4 version 5 codecs will work just fine, while others give me this annoying green bars, and complete video noise on the screen.  In VCL, I get a green bar at the top of the screen, though much of the video will seem to work normally.. 

I confess to not being a Linux pro, and am just tearing my hair out with Ubuntu lately. It seems that the minute I stabilize one thing, something else breaks.   If someone can help diagnose this, i would be grateful.

**Here is what I know**

[LIST]
[*]I have a Radeon X-series card.
[*]I the Restricted ATI drivers installed
[LIST]
[*]WHen I check System > Screen resolution, i get this message:
"The X Server does not support the XRandR extension.   *Runtime resolution changes to the display size are not available." *

I don't know if this is related or not, but it seems odd that I cannot change resolutions, when I could swear I used to be able to.  Is this a clue?
[/LIST]
[/LIST]
I don't even know how to get a report on what is installed, configured, etc, as Ubuntu doesn't have a utility for this, that I've ever found (in gnome, anyway).

So what do I do now?

---

### Post by Vaidok on 2008-11-29
I had a similar problem with my ATI video card. All I did to fix it was add the line
Option	    "TexturedVideo" "off"
to th device section of my xorg.conf file.
/etc/X11/xorg.conf

---

### Post by wheezer on 2008-11-29
> **Vaidok said:**
> I had a similar problem with my ATI video card. All I did to fix it was add the line
Option        "TexturedVideo" "off"
to th device section of my xorg.conf file.
/etc/X11/xorg.conf


Thanks.  Will try it.  Do I need a desktop restart, or a full reboot for such tweaks? (generally)

---

### Post by Vaidok on 2008-11-29
I just restarted my session with ctrl+alt+backspace.

---

### Post by wheezer on 2008-11-29
Nope. Didn't fix it

Attached is a typical opening screen from an AVI.  Is this what you saw when you had the problem?

---

### Post by Vaidok on 2008-11-29
That is different then what I had.  One thing you could try though is in vlc change the video output to X11.  I don't know if that will do it or not.

---

### Post by wheezer on 2008-11-29
> **Vaidok said:**
> That is different then what I had.  One thing you could try though is in vlc change the video output to X11.  I don't know if that will do it or not.


Well, nope.. that didn't do it.  But lo and behold, in VLC, I changed "Video Track" to "Track1" (disabled was default), and the green bar was gone, and all looks great.

I cannot find any simply setting in Totem, but suspect it must be related. I have no idea what "Track 1" refers to, as video ain't my thing.  Any ideas for how to fix Totem now?

---

### Post by Vaidok on 2008-11-29
No sorry I don't use Totem.

---

### Post by wheezer on 2008-11-29
> **Vaidok said:**
> No sorry I don't use Totem.

Now that VCL is working, i may not either. Although I do like its playlist interface better than anything else. VCL seems to ignore such niceties.

Whatever caused the track problem in VCL, must be the underlying libary (gstreamer?)., because Miro video is doing the same green bars thing.  There must clearly be something wrong under the hood. I have no idea how to debug this, and based on my history with Ubuntu, I have a hunch I have to live with it until it magically disappears.  It's days like this when windows doesn't seem too bad :(

Thanks for help!

---

### Post by Vaidok on 2008-11-29
In Miro do you use gstreamer of xine? I think it is xine by default.

---

### Post by wheezer on 2008-11-29
> **Vaidok said:**
> In Miro do you use gstreamer of xine? I think it is xine by default.

I can't seem to find any settings for it. I guess there's some config for it, becasue it's not in the interface.

---

### Post by Vaidok on 2008-11-29
It is under Video->Options->Playback.

---

### Post by wheezer on 2008-11-30
Can't find any such settings for Miro.  It must be in config somewhere.

---

