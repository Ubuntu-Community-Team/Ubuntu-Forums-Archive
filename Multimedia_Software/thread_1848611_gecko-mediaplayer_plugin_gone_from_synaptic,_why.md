---
title: "gecko-mediaplayer plugin gone from synaptic, why?"
date: 2011-09-22
forum: Multimedia Software
---

### Post by nrundy on 2011-09-22
[SIZE=2]A day or two ago Update Manager launched and required a Partial upgrade. It uninstalled gecko-mediaplayer[/SIZE].

I want to reinstall gecko-mediaplayer but it is no longer appearing in synaptic. Why?

gecko-mediaplayer is the only plugin that works to play video streams online. How can I play these streams without gecko-mediaplayer?

---

### Post by nrundy on 2011-09-23
can someone please help me out with this? I can't get any steams to play witout gecko-mediaplayer plugin and it's no longer showing up in synaptic.

---

### Post by cottfcfan on 2011-09-23
Need more info.
What version of Ubuntu are you running? What repos do you have enabled?
I'm using 11.04 & gecko-mediaplayer is in synaptic.

---

### Post by nrundy on 2011-09-24
> **cottfcfan said:**
> Need more info.
What version of Ubuntu are you running? What repos do you have enabled?
I'm using 11.04 & gecko-mediaplayer is in synaptic.

I'm using 10.04. I have Main and Universe enabled -- gecko-mediaplyer is now showing up in synaptic. But I get this message when I try to install it:

gecko-mediaplayer:
 Depends: gnome-mplayer (>=0.9.9.2) but it is not installable


when I search for "gnome-mplayer" nothing comes up except these items:
1. gecko-mediaplyer
2. gnome-subtitles
3. dvd95

Why is gnome-mplayer not installable? Anybody know a fix?

---

### Post by nrundy on 2011-09-24
I got it. I had to enable the "multiverse" repo to find gnome-mplayer. after installing gnome-mplayer, i was able to install gecko.

---

