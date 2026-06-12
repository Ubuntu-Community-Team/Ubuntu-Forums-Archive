---
title: "Rip CD with merged tracks (similar to iTunes)"
date: 2009-09-13
forum: Multimedia Software
---

### Post by Inferiority Complex on 2009-09-13
Hello.

As a recent "full-time" Linux user (I have been dual-booting for years and finally wiped everything & went for a Linux-only machine) I have been looking for alternatives for all my Windows apps and am looking for some functionality I had in iTunes that I haven't found yet under Linux.  So, I thought I'd ask everyone here.

In the past, I've used Bonkenc & Songbird to manage my MP3 music (and iPod) and whilst Songbird is available for Linux, Bonkenc has had to be switched for something else and I opted for Sound Juicer.  Both of these are currently doing a fantastic job!

For Audiobooks, I used iTunes for it's ability to join/merge multiple CD tracks as one file as it ripped them.  I have a large collection of these and I do listen to them out and about on my iPod (managed by Songbird, remember).
However, I haven't found any program under linux that has the ability to rip these CD tracks as one file.  e.g. track 1 gets ripped on it's own; tracks 2-6 become one file; tracks 7-11 become one file and tracks 12-14 become one file.

I tried iTunes under Wine but that never seemed to work properly so I'm not really willing to give that a go.  I could do this in a VM under VirtualBox but I wondered if anyone can recommend any native apps that I haven't found yet...

---

### Post by Inferiority Complex on 2009-09-16
Anyone at all able to suggest a 'rip-n-merge' program for CD tracks?

---

### Post by quack23 on 2009-09-18
[EAC]("http://www.exactaudiocopy.de/") under WINE?

I haven't tried it on jaunty (yet), but I've been using EAC on XP for years as my ripping program.  I've yet to see any linux-native program that's as capable -- but I've just installed Jaunty and haven't gotten around to checking out the ripping options yet.

---

### Post by mc4man on 2009-09-18
rubyripper has the option to output a a single .mp3
you can do the whole disk or break it up as you see fit

While you used to have to build, .debs are available

see here
[http://ubuntuforums.org/showthread.php?t=799621&page=9&highlight=rubyripper](http://ubuntuforums.org/showthread.php?t=799621&page=9&highlight=rubyripper)

post 82 links to a ppa, post 81 to the karmic forum where I attached an all-deb before the ppa was available (hardy thru  karmic, all arch's

---

### Post by rbroom on 2009-10-31
For a command-line solution, take a look at abcde (with the "-1" option).  It's quite easy to use for a command-line tool, and still gets the album info you may want from cddb.

---

