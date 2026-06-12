---
title: "Gapless playback in Rhythmbox fails"
date: 2009-05-18
forum: Multimedia Software
---

### Post by cdyson37 on 2009-05-18
The title pretty much says it all. Crossfading is enabled with a 0 second overlap, and the "on the same album" checkbox is also checked. Despite these settings, there's a noticeable pause between tracks that should continue seamlessly.

I'm using a usb sound card and a modified asound.conf to increase the buffer, but that should not affect things.

Amarok 1.4 still manages (usually) to play without gaps, although fails mysteriously is the tracks concerned are very short (circa 7 seconds).

Any help appraciated!

---

### Post by logos34 on 2009-05-18
I've never been able to get gapless output to work on ANY player EXCEPT Audacious with crossfader-plugin, which is fabulous (but mostly irrelevant for me as almost all my music with continuous tracks is in ogg vorbis or lossless format, which unlike mp3 natively supports gapless)

---

### Post by cdyson37 on 2009-05-18
I should have clarified: these are flac files. Gapless playback works perfectly in e.g. winamp, and usually on amarok (not always).

I've heard a few success stories for rhythmbox and gapless flac but it just doesn't seem to be working for me!

---

### Post by scarf on 2009-09-05
try increasing the network buffer slider to like 50% and see if that helps...if not, keep increasing it and see.  i only have mine on 128 kB and it's working all right, but different computers may need different settings! ;)

---

### Post by cdyson37 on 2009-09-05
Fantastic! I had to increase it to more than 500kb but I'm not too bothered. Possibly I need such a large buffer because it's FLAC...

I'm at a loss as to why it works when the audio is not being streamed over the network - must be a misnomer. Ah well. Thanks very much for your help!

---

### Post by Wanas on 2009-09-06
> **scarf said:**
> try increasing the network buffer slider to like 50% and see if that helps...if not, keep increasing it and see.  i only have mine on 128 kB and it's working all right, but different computers may need different settings! ;)

I was having the same problem but with all my mp3s not only Flac files, when I increased the network buffer to 500 the problem vanished thanks to the help.

But I have a question:
What is this network buffer for ? What it does when you increase or decrease ? What is its function ?

---

### Post by eddyojb on 2010-02-22
Yes, I'd also like to know exactly what network buffer really does and how strenuous it is on my (RAM?) computer when increased. As the name suggests its a buffer - but to network what? At first it suggested to me the network buffer is for sharing music with DAAC but now I see from this forum it is not.

Any ideas anyone?

---

### Post by scarf on 2010-03-08
maybe a buffer for the pulseaudio sound server?  not sure.  or maybe "network buffer" is just an incorrect name and needs to be updated.

you could load system monitor (system -> administration) and monitor your system's performance to see if it is having an impact.  i'm guessing not since we are only talking in kilobytes here...

---

