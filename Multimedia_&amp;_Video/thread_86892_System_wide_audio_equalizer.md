---
title: "System wide audio equalizer?"
date: 2005-11-06
forum: Multimedia &amp; Video
---

### Post by infinito on 2005-11-06
Hello,

I'm looking for an audio equalizer for the whole system, so i don't need to use every application equalizers, or to have one in applications that don't have it included (like totem).

Does anyone knows something llike this?

Thanks in advance!

---

### Post by obadiah on 2006-03-17
I'm looking for this as well. Has anyone found anything that will do this? I'd also like something that could add a little dimension to the sound similar to Microsoft Windows Media player's "WOW" effect. Any ideas?

---

### Post by MetalMusicAddict on 2006-03-28
I was just about to post the exact same question. Then I thought, "I better search". :)

Anyone?

---

### Post by FarEast on 2006-03-29
How about trying jack-rack with swh-plugins?
You have only to install the following with apt.
- qjackctl
- jack-rack
- swh-plugins
Visit the webs below for details;) .
[http://qjackctl.sourceforge.net/](http://qjackctl.sourceforge.net/)
[http://jack-rack.sourceforge.net/](http://jack-rack.sourceforge.net/)

Edit:
'gstreamer-editor' may be useful.

---

### Post by pdobrev on 2006-04-14
Hello there!
I've been asking myself the same question for a long time and recently I found out a satisfactory solution. I'm using oss2jack and jackd to pipe all audio through jackd and the multiband EQ plugin. However, I don't know how to enable it with jack-rack and that's why I'm using ardour (which for this purpose is just a waste of resources). So if anyone has had any luck with jack-rack, please share. I open it, choose Add plugin, tweak it around but nothing really changes.

Thanks.

---

### Post by Shay Stephens on 2006-05-10
I'm just checking in to see if anyone has found way to get a system wide equalizer working.  My sound card (on the motherboard) is putting out way too much bass.  I would love to crank the bass down some.

I am primarily using mplayer to play web radio, and I have found an equalizer in the mplayer ui, but the controls can't be changed, and I am kind of stuck ](*,)

---

