---
title: "CSS'd DVD to untouced ISO file?"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by MillDaKill on 2007-11-08
I need a ripping program that is similar to DVD Decrypter in windows but works in ubuntu 7.10.  For some reason all of the rippers I have found transcode to various formats but I just want something that will make me an untouched ISO file.

---

### Post by MillDaKill on 2007-11-08
> **veerakumar said:**
> [http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)

:popcorn:SFX: [http://www.spreadfirefox.com/?q=affiliates&amp;id=211983&amp;t=1](http://www.spreadfirefox.com/?q=affiliates&amp;id=211983&amp;t=1):)

Is there guide how to go to an ISO, I have tried this program and it only seems to transcode?

---

### Post by disturbedite on 2007-11-08
dvd decrypter in wine runs flawlessly.  you just have to know where to find it...

---

### Post by netyire on 2007-11-09
Just install wine (its in the repos) and you can run DVD decrypter with wine on like you can on Windows. Or you can try installing libdvdcss (if its legal in your country) before utilizing kde to create an image of the disc.

---

### Post by chriv on 2008-02-02
I had to try half a dozen programs before I found one that just works.  So far, k3b seems to be the absolutely easiest point-and-click method of just ripping a DVD movie to an ISO image, without f***ing around with it, re-encoding it, shrinking it, messing with the menus, or anything else.  It doesn't have all the features of DVDDecrypter, but it is open source, and it is a pure rip.  I've used so far to rip 3 DVDs (not exactly a large testbed), and had no problems ripping.

Why in the heck is it that Automatix doesn't tell you about this one?  For Pete's sake, automatix will install a program called "DVDRip", but it's not really just a ripper.  It's a ripper and reencoder.  If you're going to go to all the trouble to rip the disc and reencode it, then why not give me the option to stop before the reencoding?

I cannot believe how hard it was to find such a simple feature in Linux.

k3b, as the name implies (it starts with a "k") is designed for the KDE environment.  However, like most other KDE programs, it works just fine in Gnome, and therefore, just fine in the default Ubuntu environment.

Since I found this program on about my 10th or 20th attempt at finding a program that would just rip a DVD Movie to an ISO image, let's see if this statement helps with search engine placement:

To rip a DVD Movie to an ISO in ubuntu (or any other linux), I recommend using the package k3b.  k3b has an easy to use GUI which can be used to make an ISO rip from a DVD.  It is free (I believe it is GPL).

Maybe this will save you and a few other people all the headaches I went through for such an easy answer.

And to the developers of all the other dvd "ripping" programs out there:  Re-encoding, shrinking, transcoding, menu manipulation, and IFO editing are NOT part of ripping.  They are add ons/extras.  If you are going to put the name "rip" in your title or your package description, you should have the ability to just rip the whole disc, with nothing else forced down your throat!

---

