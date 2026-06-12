---
title: "banshee"
date: 2011-02-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-02-11
just notice that if you click on the volume control it is a slider and an option to open banshee is below the slider followed by sound preferences

---

### Post by cariboo on 2011-02-11
That's been around for quite a while, if you start up rhythmbox, it shows up in the sound menu.

---

### Post by rburkartjo on 2011-02-12
tks

---

### Post by andrek on 2011-02-12
Funny thing is, I have Banshee listed twice in there. While playing, only one of them gets track info and control buttons. Is this normal?

//edit

Fixed by 
gsettings reset com.canonical.indicators.sound interested-media-players
and
gsettings reset com.canonical.indicators.sound blacklisted-media-players

---

### Post by rburkartjo on 2011-02-12
and, only have it listed once on my end

---

### Post by VinDSL on 2011-02-27
> **andrek said:**
> Funny thing is, **[COLOR="Red"]I have Banshee listed twice in there[/COLOR]**. While playing, only one of them gets track info and control buttons. Is this normal?

//edit

Fixed by 
gsettings reset com.canonical.indicators.sound interested-media-players
and
gsettings reset com.canonical.indicators.sound blacklisted-media-players
Can you expand on this?

I'm getting GLib-GIO-ERROR's when I tried your fix(es).

I've noticed this 'double loading' problem crops up, in both 10.10 & 11.04 when you tick the "Show Banshee in the sound menu" option in the Banshee prefs.

Thus, it *seems* like a bug in Banshee.

It's very irritating!

Unticking the 'sound menu' option takes care of the problem.

---

