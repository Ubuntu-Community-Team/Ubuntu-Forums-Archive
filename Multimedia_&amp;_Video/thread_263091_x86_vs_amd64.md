---
title: "x86 vs amd64"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by subpar on 2006-09-22
When installing ubuntu to be used as a studio, would it be wiser to install it as amd64 (since I use an amd 64 chip in my computer), or to install an x86 system? I've read a few things about problems with wine on amd64, and I would most likely need to use that to run Sibelius, and perhaps Reason (though I hope that I can bypass using reason with an open source software package).

What experiences have you guys had that are running with amd64 as far as performance and problems getting certain softwares to work? Thanks for any input!

---

### Post by dolson on 2006-09-22
I think you're going to have major problems trying to run big Windows studio apps like that in Wine. Basically, leave Windows apps in Windows, especially when it comes to something like audio stuff.

I think that 32-bit mode is currently better for audio. I hear a lot of complaints from other 64-bit users, but then again, that was back in Breezy's day. Those people have since deleted me from their MSN lists, according to Gaim, so I can't be bothered to keep up with them and their experiences.

I use 32-bit at work on my 64-bit PC, just because. I don't feel I'm missing out on anything.

Your call though. You could start with 64-bit and if you don't like it, reinstall.

---

### Post by subpar on 2006-09-22
I've been running amd64 for about two months, and I hardly ever use windows anymore, which is why I want to get rid of it. The only program I'm really worried about is Sibelius, nothing TOO resource heavy like Reason or Cubase, since from what I've seen at the wiki, a lot of the stuff that I did with those programs can be done with open source software, and besides, whatever limitations may be imposed on me by switching completely to linux will just mean more of a challenge :).

---

### Post by dolson on 2006-09-22
Heh, good attitude. That's how I feel a lot too now. I just can't be bothered to care about what I'm missing out on. I really can't afford to buy those big apps anyhow, so I'm grateful to have less functionality for free.

What is Sibelius anyhow? Maybe there's something similar in Linux that will do what you need.

---

### Post by Cybolic on 2006-09-23
I haven't tried Sibelius, but looking at its screenshots, I imagine either [Lilypond]("http://lilypond.org/web/") or [Rosegarden]("http://www.rosegardenmusic.com/") might do the trick for you - none of them have automated creation of backing instruments, but if you really need that there are a few programs available for that, try looking through [Sound & MIDI Software For Linux]("http://sound.condorow.net/")s [Musician's Utilities]("http://sound.condorow.net/mut.html") page, and you might find something you can use.

---

### Post by tuxcantfly on 2006-09-23
actually, you can use wine if you get the i386 version from [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com)

then you force install it sudo dpkg --force-all -i ./wine*

---

### Post by subpar on 2006-09-24
> **Cybolic said:**
> I haven't tried Sibelius, but looking at its screenshots, I imagine either [Lilypond]("http://lilypond.org/web/") or [Rosegarden]("http://www.rosegardenmusic.com/") might do the trick for you - none of them have automated creation of backing instruments, but if you really need that there are a few programs available for that, try looking through [Sound & MIDI Software For Linux]("http://sound.condorow.net/")s [Musician's Utilities]("http://sound.condorow.net/mut.html") page, and you might find something you can use.

I've worked with lilypond a lot, on contributions towards the [mutopia project]("http://mutopiaproject.org"), but for personal works, sibelius just seems to rub me better (it must be the point click atmosphere of it). I haven't looked at rosegarden, but I'll be doing that soon. Thanks for the suggestion!

> **tuxcantfly said:**
> actually, you can use wine if you get the i386 version from [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com)

then you force install it sudo dpkg --force-all -i ./wine*

I tried that, but when I did winecfg, it spat out all sorts of errors, and I didn't know where to start to fix it. It doesn't matter though, since I went ahead and decided to go with i386, and now have computer set up with that version of the distro.

---

### Post by subpar on 2006-09-24
> **dolson said:**
> Heh, good attitude. That's how I feel a lot too now. I just can't be bothered to care about what I'm missing out on. I really can't afford to buy those big apps anyhow, so I'm grateful to have less functionality for free.

What is Sibelius anyhow? Maybe there's something similar in Linux that will do what you need.

Sibelius is notation software, much like lilypond, except you place notes with point and click, instead of writing it to a file and then through a parser. Also, what I really enjoyed about it was realtime midi playback, which meant I could write down a section of music, say about 8 measures or so, and then play it back. Very useful for someone who doesn't have a piano to pound stuff out on.

---

### Post by dolson on 2006-09-24
I think Denemo does the point and click stuff.

---

### Post by goodmanbrown on 2006-09-26
noteedit also does point-and-click score editing with midi playback.  I've been pretty happy with it.

---

### Post by dolson on 2006-09-26
Looks like NoteEdit is discontinued? [http://rnvs.informatik.tu-chemnitz.de/~jan/noteedit/noteedit.html](http://rnvs.informatik.tu-chemnitz.de/~jan/noteedit/noteedit.html)

EDIT: At first I tried the Berlios site, and it was going to 404 Not Found, but now it's working again.

Here's a screenshot of NoteEdit:
[img]http://noteedit.berlios.de/img/noteedit_main.png[/img]

Here's a screenshot of Denemo:
[img]http://denemo.sourceforge.net/0.7.3beta2-4tet.png[/img]

I don't use either of these apps, so try them both if the first one you try doesn't do what you need.

---

