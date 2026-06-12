---
title: "Playing realaudio .ram files in mplayer"
date: 2008-05-16
forum: Multimedia Software
---

### Post by apokkalyps on 2008-05-16
Ordinarily I use VLC player and just dont mess with codecs because it usually works for everything, but I've just hit a snag with it and it plays realaudio files poorly.  So I installed mplayer and all the restricted codecs, medibuntu, w64codecs, and all the updates.  I'm trying to set it up so that when i stream tracks off of dancerecords.com they will open a working program and actually play.

Well I after all these codecs and everything I got mplayer where it can play .rm files.  But .ram files are basicly text files that have a url inside to stream a .rm file.  Mplayer still can't do what I need it to do for playing ram files off the internet because it apparently doesn't know how to open the ram file and get the .rm url out and play it.  Is there any workarounds for this?

Also, apparently mplayer doesnt support drag and drop playing?  Isn't it supposed to be this awsome player?  Thats kinda lame IMO, but either way I'm only trying to use it for these realaudio files.

---

### Post by andrew.46 on 2008-05-22
Hi:

> **apokkalyps said:**
>   Mplayer still can't do what I need it to do for playing ram files off the internet because it apparently doesn't know how to open the ram file and get the .rm url out and play it.  Is there any workarounds for this?

MPlayer opens ram files with the following syntax:
```

$ mplayer -playlist filename.ram
```

   Andrew

---

### Post by apokkalyps on 2008-05-23
AH ok thanks alot!

Is there a way I can set firefox to open ram files off the internet automatically with that command?

---

### Post by andrew.46 on 2008-05-24
Hi:

> **apokkalyps said:**
> AH ok thanks alot!

Is there a way I can set firefox to open ram files off the internet automatically with that command?

There is a third party program that should do this, although I don't use it myself. This is the [mplayer-plugin program]("http://mplayerplug-in.sourceforge.net/faq.php") that the Ubuntu repository calls 'mozilla-mplayer'. I have no experience with this but I believe these forums should have some more info.

            Andrew

---

### Post by chochem on 2008-05-24
Uhm you do know that you can install realplayer to complement VLC, thus avoiding the whole codecs quagmire? Mind you it doesn't seem to b in the hardy 'partner' repos or any other repos for that matter, but user jean1963 has kindly made a package available in [this thread]("http://ubuntuforums.org/showthread.php?t=758024"). RP11 for linux is a pretty boring player but considering all the 'interesting' things that RP for Windows tries to do for you, that's actually a good thing :)

---

### Post by apokkalyps on 2008-05-26
Thanks guys I got it working!

---

