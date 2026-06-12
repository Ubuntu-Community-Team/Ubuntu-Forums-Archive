---
title: "VLC Media Player 1.1.9 in Ubuntu 10.04"
date: 2011-07-08
forum: Multimedia Software
---

### Post by Objekt on 2011-07-08
Is there any way to install VLC Media Player 1.1.9 in Ubuntu 10.04?  I was using VLC 1.1.10, but it has a weird audio/video sync bug that may be solved by rolling back to 1.1.9.  However, I can't find any way to do that.

I tried removing the "lucid-bleed" repository from my Sources, but now Software Center only offers VLC 1.0.6.  

Likewise I tried a walkthrough to "install VLC 1.1.9" but it didn't work: [http://www.ubuntugeek.com/how-to-install-vlc-1-1-9-using-ubuntu-ppa.html]("http://www.ubuntugeek.com/how-to-install-vlc-1-1-9-using-ubuntu-ppa.html")

I followed the instructions precisely, but got VLC 1.0.6.

So how can I get VLC 1.1.9 installed?

---

### Post by BicyclerBoy on 2011-07-08
I would think that the previous versions are still available in lucid-bleeding.

You could re-instate the bleeding repos/filter.
You can then search/find VLC package (in synaptic manager) & then force a version.
Then lock that version.

---

### Post by Objekt on 2011-07-08
Unfortunately, only 1.0.6 and 1.1.0 are offered through the lucid-bleed ppa.

---

### Post by BicyclerBoy on 2011-07-08
My mistake..
Just checked the 10.04 box & vlc 1.0.6 is the latest in lucid-proposed.

By lucid-bleeding do you refer to unsupported updates (lucid-backports) or an additional ppa/repos ?

Can you not force a version thru' synaptic from n-muench's ppa ?
(I'm tempted to try myself)

---

### Post by Objekt on 2011-07-08
"lucid-bleed" is the name of the ppa.  I can force a version when using this ppa, but my only choices are VLC 1.0.6 (in two slightly different flavors) or VLC 1.1.10.

Tried the other one as well (muench's ppa) as instructed in the link above; got 1.0.6.

---

### Post by BicyclerBoy on 2011-07-08
I found it as well...lucid-bleed is referred to here
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

As they say it is limited to 1.0.6 for lucid.

It seems VLC is going thru' some pain with pulseaudio/alsa/linux audio..
I thought a work-around was to use alsa directly ?

---

### Post by Objekt on 2011-07-08
Not sure whether that's possible, but may be worth a try.

I don't understand why this new problem has occurred.  VLC 1.0.5 through 1.1.9 worked just fine with PulseAudio, at least for me.

---

### Post by BicyclerBoy on 2011-07-08
It is possible to output direct to alsa device or plughw or plugin.
I have VLC pointed at alsa always so that AC3/DTS pass thru' works.
But I don't care about audio sharing or system sounds.

---

### Post by Objekt on 2011-07-14
I found the place where I can select ALSA output.  However, if I do that, I don't get any sound from VLC at all.  So that doesn't really fix the problem.

---

### Post by ron999 on 2011-07-14
Hi
I have VLC-v1.1.9 installed with Lucid Lynx 10.04.
Compiled using the guide here:- [http://ubuntuforums.org/showthread.php?t=1398119]("http://ubuntuforums.org/showthread.php?t=1398119")
Follow the instructions as if building v1.1.10 but use v1.1.9 source code, and FFmpeg-0.7.1 source code instead of FFmpeg-0.8.

---

### Post by Objekt on 2011-07-15
Not going to help.  I removed VLC 1.1.10, installed 1.0.6, but still had the same problem.  So I doubt 1.1.9 would be any different.

However, apparently it IS possible to get VLC 1.1.9 in Ubuntu 10.04, which does answer my question.  So I'm calling this one "solved."

---

