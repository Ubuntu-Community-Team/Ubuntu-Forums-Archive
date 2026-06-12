---
title: "Gapless audio players that actually work - they do exist, right?"
date: 2010-03-01
forum: Multimedia Software
---

### Post by Quasarsphere on 2010-03-01
OK, so I seem to be at something of a dead end in my quest for an audio player that will actually play gapless.

XMMS2, with the crossfade plugin will play gapless...assuming it will play at all.  Sometimes I can get it to work when I end pulseaudio, and sometimes not.  And now it's just not working at all.

Audacious has a crossfade plugin that I'm informed works with gapless...but as soon as I install the plugin, audacious just stops working.

MOC claims to have gapless support, but now that I've (supposedly) successfully installed it, I am buggered if I can find it on my computer.

Guayadeque, which I found out about in the last ten minutes, is said to work with gapless, but having followed the detailed instructions on how to install it, I cannot get it to install.  I keep getting some crap about "wxWidgets not found"

Rhythmbox is claimed to have gapless support.  It doesn't.

Exaile is supposed to have some kind of gapless/crossfade thing, but it doesn't seem to do anything at all.

Aqualung will do gapless, and at a pinch I'll use it, but if I want to skip to the next track or adjust the volume, at least fifteen seconds will elapse between me telling it to do something, and it doing what it's bloody well told!

Is there any gapless audio player that actually plays gapless?

---

### Post by amrypma on 2010-03-01
you start moc in a console.
Applications -> Accessories -> Terminal (just in case)
the command is actualy mocp, I have no idea why.

you'll have to learn some keybindings.
if you start mocp and type '?' you'll get the list.
you should read it, there are some odd ones.

---

### Post by sojyujai on 2010-03-01
I know your pain.  

I've been waiting for what seems like years for Banshee to support gapless playback - it looks like it should be ready soon, you can follow their progress here:
[https://bugzilla.gnome.org/show_bug.cgi?id=440952]("https://bugzilla.gnome.org/show_bug.cgi?id=440952")

In the meantime I've just been using the cross-fading backend in Rhythmbox.  I'm not sure, it may not be true gapless but it works acceptably well enough for me for the time being.

I've never tested it but I thought I read that Songbird supported gapless playback.

---

### Post by Quasarsphere on 2010-03-01
> **amrypma said:**
> you start moc in a console.
Applications -> Accessories -> Terminal (just in case)
the command is actualy mocp, I have no idea why.

you'll have to learn some keybindings.
if you start mocp and type '?' you'll get the list.
you should read it, there are some odd ones.Aw, sweet, cheers!

It's an odd one, isn't it?

It handles gapless OK...not brilliant, but OK...

I'm going to be very anal about this issue, because before I upgraded from 8.10 to 9.04 I had everything working just the way I liked it.  XMMS was excellent back then.

---

### Post by Quasarsphere on 2010-03-01
> **sojyujai said:**
> I know your pain.  

I've been waiting for what seems like years for Banshee to support gapless playback - it looks like it should be ready soon, you can follow their progress here:
[https://bugzilla.gnome.org/show_bug.cgi?id=440952]("https://bugzilla.gnome.org/show_bug.cgi?id=440952")

In the meantime I've just been using the cross-fading backend in Rhythmbox.  I'm not sure, it may not be true gapless but it works acceptably well enough for me for the time being.

I've never tested it but I thought I read that Songbird supported gapless playback.I haven't been able to get the Rhythmbox cross-fading backend to do anything at all.

---

### Post by Quasarsphere on 2010-03-01
I bit the bullet and upgraded to Karmic.  It comes with Audacious2 which has a crossfade/gap killer plugin with it.  Very cool.  Would be even more cool if it actually worked.

Also, I was able to install Guayadeque.  Looks great.  Apparently it supports gapless playback.  How do you get it to do that?

**Another update:** It seems that what annoyed me about Aqualung is no longer an issue.  So, while I have something of a soft spot for Audacious, it looks like I'll be sticking with Aqualung for now.  It's the only one that really does gapless properly.

---

### Post by Uncle Spellbinder on 2010-03-01
Ooooops. Wrong thread. Sorry.

:oops:

---

### Post by Henry Flower on 2010-03-01
If you (or anyone) still fancies experimenting:

- mpd is gapless.  Lots of clients are available, and if you have the right mindset, the satisfaction of getting the thing working is worth the hassle. ;)

- the newest version (2.2) of quod libet is said to be gapless, though I haven't tried it myself.   The version in the repos is 2.1, so you'd have to get 2.2 from elsewhere.   

- gmusicbrowser seems to be gapless, but with some instability issues: [http://forum.gmusicbrowser.org/index.php?topic=83.0](http://forum.gmusicbrowser.org/index.php?topic=83.0)  I remember the last time I looked at that one it seemed very promising, so I hope it continues to improve.

---

### Post by amano on 2010-03-26
Apparently Banshee will be gapless. At least the upcoming version 1.6.

But not for mp3s.

Did anyone get gapless mp3 support with ANY player working on linux? Ever?

---

### Post by hugmenot on 2010-03-28
> **amano said:**
> Did anyone get gapless mp3 support with ANY player working on linux? Ever?

Yes, get it here: [https://edge.launchpad.net/~lazka/+archive/ppa](https://edge.launchpad.net/~lazka/+archive/ppa)

It has power features not found elsewhere. Give it a shot.

---

### Post by cchhrriiss121212 on 2010-03-29
> Yes, get it here: [https://edge.launchpad.net/~lazka/+archive/ppa]("https://edge.launchpad.net/%7Elazka/+archive/ppa")

It has power features not found elsewhere. Give it a shot. 	

This is excellent thanks for posting. Gapless with flac and nearly gapless with mp3s, the tagging system is also the best I've seen.

---

### Post by hugmenot on 2010-03-29
BTW, you might find interesting where QL gets its release codenames from:

[http://code.google.com/p/quodlibet/source/browse/quodlibet/NEWS](http://code.google.com/p/quodlibet/source/browse/quodlibet/NEWS)

---

