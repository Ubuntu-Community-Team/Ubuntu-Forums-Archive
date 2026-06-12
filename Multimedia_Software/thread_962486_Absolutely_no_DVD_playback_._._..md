---
title: "Absolutely no DVD playback . . ."
date: 2008-10-29
forum: Multimedia Software
---

### Post by ickyfeet on 2008-10-29
I cannot, for the life of me, get any commercial DVD to play on my computer.  I'm running Intrepid Ibex RC and have installed all the required software (libdvdread3 libdvdnav4 libdvdcss2) and my computer still fails to acknowledge that a DVD was inserted into the drive.  I can read DVDs that have data on them but nothing with any type of video.  Any help would greatly appreciated.  Thanks in advance.

---

### Post by aeiah on 2008-10-29
if all codecs installed correctly, have you tried manually trying to play the dvd from your media player of choice? perhaps its simply not auto-running dvds

---

### Post by lviggiani on 2008-10-29
Hi,
I had a simila problem with Ubuntu in English and commercial DVD's in italian.
Mine was a problem of DVD region settings.
The answer was *regionset*
Have a look [_here_]("http://ubuntuforums.org/showthread.php?t=921245&page=2"), at the end of the thread.
I hope that this will help.

---

### Post by ickyfeet on 2008-10-29
No dice on either count.  I've tried opening DVDs in VLC and Totem.  Both say that nothing is media is mounted.  I try to mount the DVD from the CLI and it gives me an error amounting to "There is no media in the drive".

I also tried regionset and it tells me that there must be some type of readable media in the drive before I can continue.

Thanks for the suggestions.

---

### Post by cariboo on 2008-10-29
Have you set your dvd device to /dev/sg0 in File-->Open Disk-->Disk-->Customize? This assumes you are using version 0.8.6

Jim

---

### Post by ickyfeet on 2008-10-29
Which program are you talking about?  I tried opening /dev/sg0 in gxine, vlc and totem.  Still nothing . . .

---

### Post by Bablefish on 2008-10-29
Maybe you should look in to Automatrix

---

### Post by ickyfeet on 2008-10-29
Automatix isn't really an option for me.  I don't like the way it handles package installation.  I'm at the point now that I want to know what's causing this to happen rather than a quick work around.

---

### Post by ickyfeet on 2008-11-08
Bump

---

