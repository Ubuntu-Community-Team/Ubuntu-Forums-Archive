---
title: "Slow-Motion mkv"
date: 2009-06-22
forum: Mythbuntu
---

### Post by adambomb42x on 2009-06-22
I have some mkv files that play in slow-motion with the internal player in Mythbuntu 9.04. Not all of the mkv files play slow and those that do play slow, play fine in VLC on my windows machine.
Please help, I'm on the verge of reimaging.

---

### Post by ian dobson on 2009-06-22
Hi,

I had problems playing mkv (1080p) files on my frontend until I set VPDAU as the default decoder for mplayer. Note I'm using the VDPAU backports version of mythtv not the standard mythbuntu package.

Regards
Ian Dobson

---

### Post by newlinux on 2009-06-22
I've had problems with some mkv files using the Internal player as well. Rather than reimaging, why not consider using VLC or mplayer in Linux for these files? That's what I do for some of the files that the internal player has problems with.

I assume you have already ruled out potential networking problems as an issue.

---

### Post by adambomb42x on 2009-06-22
I'm stuck using only the internal player for now because that is all that MythPyWii works with. 
This really seems like a codec issue because it only happens with this one video that in the past has played fine. It is also not lag, it is truly playing in slowmo. It's really weird.

---

### Post by newlinux on 2009-06-23
take a look at your frontend logs when playing back the video... maybe it will tell you what is going on (might want to turn up the verbosity with -v playback).

---

