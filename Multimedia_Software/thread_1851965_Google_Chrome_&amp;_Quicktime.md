---
title: "Google Chrome &amp; Quicktime"
date: 2011-09-29
forum: Multimedia Software
---

### Post by mang0 on 2011-09-29
[SOLVED]
Installed gecko-mediaplayer from terminal (it's also in synaptic package manager) and it ran perfectly.

-----------------------------------------------------------------

Hey everyone, I've got a problem with Chrome and Quicktime movies (.mov and .avi). 

For my work, I need to be able to view .movs in chrome, but I can't seem to get it to work. I've got mplayer, ubuntu-restricted-extras, w32codecs and the VLC plugin. However, When I look at an embedded .mov, I get this error;

This content requires the QuickTime Plugin. Download QuickTime Player.
Already have QuickTime Player? Click here.

I've tried all sorts, opening the file directly in Chrome, but that just takes me to download it, I've tried disabling the VLC plugin (saw that on another thread on here)but to no avail. Any help greatly appreciated!

-mang0

---

### Post by An Sanct on 2011-09-29
If you are using a 64bit OS, try [this]("apt://w64codecs").

---

### Post by mang0 on 2011-09-29
And if I'm using 32 bit? I've got the 32bit version of that installed, not doing anything :/

---

### Post by An Sanct on 2011-09-29
Well, it depends on the "bitness" of your OS, install the correct library (32b/64b)

Anyhow, w32codecs/w64codecs is handling QuickTime media. To check out if you have the codecs installed properly, download a mov and play it locally. If this does not work, your problem is elsewhere (not with chrome)

PS. for ease of helping, tell us your Ubuntu version (don't forget the 32/64 bit part)

---

### Post by mang0 on 2011-09-29
Well, it is listed under my name ;) Ubuntu 11.04 Natty Narwhal, 32 bit. 

I've fixed it though. Installed gecko-mediaplayer, and it works without a hitch :D

---

### Post by An Sanct on 2011-09-29
Glad to hear that ;)

---

