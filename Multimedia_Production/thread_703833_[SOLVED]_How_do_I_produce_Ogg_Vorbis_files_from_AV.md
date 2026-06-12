---
title: "[SOLVED] How do I produce Ogg Vorbis files from AVIs?"
date: 2008-02-21
forum: Multimedia Production
---

### Post by wayfarer51 on 2008-02-21
I have several AVI files I ripped from a concert DVD using AcidRip.  I'd like to know how I can extract the audio portion to Ogg Vorbis files.  I was going to use transcode to take the Oggs right off the DVD, but I couldn't find one that didn't give me errors for unresolved dependencies for which I couldn't find the missing files. ](*,)

So, if you know how to do it, will you help me out?  Thanks for your help.

Neill

---

### Post by gsmanners on 2008-02-21
Isn't transcode in the repo? It installed just fine for me.

---

### Post by em3raldxiii on 2008-02-21
Hmm, I have never done that specifically, but I have a feeling that a program called AVIDEMUX might be just the ticket.  I use it a lot for a number of different video related situations.

Basically, open your ripped AVI file with AVIDEMUX (which is a graphical app) and then there are a couple of rather simple steps to exporting (or saving) the new files in a number of different configurations.  Usually I just use it for converting the audio/video from one to another type ... but I think you could just choose to save the audio (or select nothing for video?).  Then, regardless of the type of audio file you end up with, you should be able to use something to convert it to ogg vorbis.  Perhaps the mplayer CLI or something.

You could also look at mencoder for command-line tools that MIGHT do what you want.

---

### Post by wayfarer51 on 2008-02-22
Hey!! Avidemux worked nicely!  The app seemed pretty complex to me, so I was glad to find the precise instructions on how to do it.  I couldn't convert directly to Ogg, but I saved them to LAME and then ran them through Gnormalize [http://gnormalize.sourceforge.net/]("http://gnormalize.sourceforge.net/").  

Here's how to do it: [http://www.avidemux.org/admWiki/index.php?title=Save_only_audio  Wiki]("http://www.avidemux.org/admWiki/index.php?title=Save_only_audio")

I suspect Avidemux may be able to get the audio only straight from the DVD itself by chapter and titlechapter.

Thanks to both of you for your responding.

Neill

---

### Post by em3raldxiii on 2008-02-22
Glad to help!  Thanks for letting us know exactly how you got it all to work.

PS.  I love your avatar image ... cute :D

---

