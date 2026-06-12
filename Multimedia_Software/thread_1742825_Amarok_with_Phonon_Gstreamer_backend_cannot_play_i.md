---
title: "Amarok with Phonon Gstreamer backend cannot play internet streams."
date: 2011-04-29
forum: Multimedia Software
---

### Post by CyberAngel on 2011-04-29
Anyone else experiencing this problem?

I am on Kubuntu Natty 11.04 64 bit.

I try to play some internet streams but when gstreamer is used as the phonon backend, Amarok never plays them.
With Xine or VLC backend looks like I have no problems...

Exactly below you can find two of the streams I am trying.

mms://a1251.l4434923250.c44349.g.lm.akamaistream.net/D/1251/44349/v0001/reflector:23250

mms://best.live24.gr/best1222?MSWMExt=.asf

---

### Post by el_koraco on 2011-04-29
Nope, playing it just fine here. I mean, both your streams. And the offered ones too.

---

### Post by CyberAngel on 2011-04-29
> **el_koraco said:**
> Nope, playing it just fine here. I mean, both your streams. And the offered ones too.

hmmmm
Strange..
Did you make a fresh installation or an upgrade from 10.10?

---

### Post by el_koraco on 2011-04-29
I did a 32 bit clean install a couple of weeks ago. I'm not all that surprised you're experiencing such issues, the Gstreamer back-end is new in Kubu, and pulseaudio is not a 100 percent integrated with KDE. You might try installing pavucontrol and padevchooser and mess around with other sound card options in Phonon. 

You're not alone in having sound problems, though, there's a Skype related issue, and I personally can't play flash audio through my USB speakers.

---

### Post by CyberAngel on 2011-04-29
> **el_koraco said:**
> I did a 32 bit clean install a couple of weeks ago. I'm not all that surprised you're experiencing such issues, the Gstreamer back-end is new in Kubu, and pulseaudio is not a 100 percent integrated with KDE. You might try installing pavucontrol and padevchooser and mess around with other sound card options in Phonon. 

You're not alone in having sound problems, though, there's a Skype related issue, and I personally can't play flash audio through my USB speakers.

Well.... I think that I will stick with VLC backend then :)
Thank you

---

### Post by nortexoid on 2011-04-29
A different issue (and known bug) with the gstreamer backend is that Amarok can't scan files. I'm using the vlc backend without any problems. This is a pretty serious bug if you ask me.

---

### Post by el_koraco on 2011-04-29
Scan local files?

---

### Post by nortexoid on 2011-04-30
Yes, scan local files like mp3s, by which I mean skip ahead e.g. 10 seconds in a song.

---

### Post by trtr on 2011-06-25
> **CyberAngel said:**
> Anyone else experiencing this problem?

I am on Kubuntu Natty 11.04 64 bit.

I try to play some internet streams but when gstreamer is used as the phonon backend, Amarok never plays them.
With Xine or VLC backend looks like I have no problems...

Exactly below you can find two of the streams I am trying.

mms://a1251.l4434923250.c44349.g.lm.akamaistream.net/D/1251/44349/v0001/reflector:23250

mms://best.live24.gr/best1222?MSWMExt=.asf

Same problem here. With Somafm radio and others. I try amarok with debug mode and I can read some problems with the metadata. Sometimes I can listen the stream but the datas is empty.

No problem with VLC backend.

---

