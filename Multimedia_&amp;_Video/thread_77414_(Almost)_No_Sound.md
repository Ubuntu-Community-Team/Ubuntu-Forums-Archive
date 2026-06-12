---
title: "(Almost) No Sound"
date: 2005-10-16
forum: Multimedia &amp; Video
---

### Post by mdognrdog on 2005-10-16
I've got a weird sound problem on my ThinkPad T40 (which has an Intel AC97 onboard sound chip), and it's tough to figure out through the usual routes what's going on.

If I'm in a terminal, and do something that's not permitted, like pressing backspace when I'm at a prompt, I hear the error bell.  If I pull the power cord or close the lid, I get the beeping sound.  So both at the hardware level, and at whatever level the terminal is sending out error messages, I've got sound.

But nothing in X except gnome-terminal makes any noise.  If I run the "Multimedia Systems Selector," and test the ALSA sink, it doesn't indicate that it thinks the ALSA pipeline is broken.  It opens the little "testing pipeline" window (it does NOT say it can't open a pipeline), but the computer is still totally silent.

It's not a permissions problem.  Multimedia programs run as root ALSO don't have sound.  It's not something with alsamixer; ALSA sees the card, and alsamixer lets me unmute all channels.  Still completely silent.  :confused: 

Does anybody have any ideas?

---

### Post by kombipom on 2005-10-17
Some threads have suggested muting the IEC bits in alsamixer, you could give that a go.

Kombipom

---

### Post by mdognrdog on 2005-10-17
I don't even have any 'IEC' control in alsamixer, so that ain't it...

---

### Post by ecobuntu on 2005-10-17
[QUOTE=mdognrdog]I don't even have any 'IEC' control in alsamixer, so that ain't it...[/QUOTE]

run @ terminal: alsaconf

choose your card

run @ terminal: alsamixer

run @ terminal:  alsactl storeal

[/code]

[code]

---

### Post by kombipom on 2005-10-19
I can't find alsaconf anywhere on my system or in the repositories.:confused:

---

