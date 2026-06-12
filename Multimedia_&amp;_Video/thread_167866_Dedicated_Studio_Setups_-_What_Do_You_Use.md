---
title: "Dedicated Studio Setups - What Do You Use?"
date: 2006-04-29
forum: Multimedia &amp; Video
---

### Post by TDave on 2006-04-29
All

Really just a general enquiry to find out what sort of hardware you folks are running your Ubuntu Studios with, and any difficulties / workarounds you needed to do, if any.

I appreciate that the Wiki has some information on a couple of things, but as an 'outsider' looking in to the Studio idea (with a view to maybe playing with things when I get home / get money) I'm curious what sort of setups people are using.
Presumably most setups that work within the Ubuntu setup would work with other Linux Dsitros as a base (dynebolic and the like) with minor tweaks.

Alternatively if people have links to information that I've missed (my online time is somewhat limited for searching too long and hard atm) that too would be appreciated.

Many thanks.

---

### Post by dolson on 2006-04-29
Well, my info is on the wiki, which you already read. My sound cards aren't great, but they work ok for me. I'd like to get an RME Hammerfall someday though.

It'd be nice if the hardware section was expanded. Actually, it'd be nice if the entire wiki was expanded...

---

### Post by .t. on 2006-04-30
Well, at the moment I'm running Dapper on a Dell Inspiron 6000 with a Creative SoundBlaster Audigy 2 ZS Notebook card as my sound I/O. It only has one analog/digital input, so I'm gonna have to get a mixer (probably a Yamaha MG-10/2 or alike) and a USB MIDI keyboard, which will be the E-MU Xboard49. From what I hear, all this equipment works well.

However, there is one bug which conflicts ~/.asoundrc.asoundconf and /var/lib/alsa/asound.state, causing ALSA applications to sometimes fail. Nonetheless, I've filed it, and I'm sure it will get fixed. At the moment, just comment out the line in your ~/.asoundrc that includes .asoundrc.asoundconf, it's a pretty dirty hack though - as your soundcard select option will be disabled.

---

