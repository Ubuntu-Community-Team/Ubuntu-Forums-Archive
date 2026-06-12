---
title: "Amarok AMD64 always crashing on startup"
date: 2012-01-11
forum: Multimedia Software
---

### Post by iflanery on 2012-01-11
Being in possession of a borked Windows 7 installation, I loaded the AMD 64 version of Kubuntu Oneiric on my HP G42 laptop last night, and with proper drivers (and cracks) installed, managed to get OpenGL working.

This afternoon, I decided to get Amarok configured, which involved getting my music from my aging Dell Inspiron 530n onto my decidely newer laptop.

Getting the music proved painless enough, and the initial Amarok scan took something like 45 minutes after I assumed everything would proceed as it ordinarily would.

I was wrong.

After everything scanned, I attempted to play something from my collection, which failed miserably and Amarok crashed after a few seconds. Now, every time I open up Amarok, it crashes within a few seconds. I can't even configure it to use the phonon-backend-vlc.

Any thoughts as to how I can get Amarok working again?

Relevant specs are as follows:

Intel Core i3 processor, 2.26 gHz.
320 GiB HDD
3 GiB RAM
Intel i915 Integrated Graphics

Thanks in advance!

---

### Post by inobe on 2012-01-11
when apps thrash back at you like that, you can either file a bug report

[https://launchpad.net/~kubuntu-bugs](https://launchpad.net/~kubuntu-bugs)

**or**

you can try and get a newer app that has been fixed by upgrading!

the good thing about kubuntu, the kde desktop can be upgraded, everything from it's plasma workspace to it's applications...

[http://www.kubuntu.org/kde-sc-474](http://www.kubuntu.org/kde-sc-474)

that upgrade above will get you to kde version 4.7.4, once there, it's possible to get amarok 2.5 from backports.

[http://www.kubuntu.org/news/amarok-25-backports-ppa](http://www.kubuntu.org/news/amarok-25-backports-ppa)

not certain if they recently included amarok 2.5 in the plasma desktop repo, after upgrading to 4.7.4, see what version of amarok you have before adding the amarok ppa...

you have some choices:)

---

### Post by iflanery on 2012-01-11
I suppose I'll try what you suggested tomorrow. For right now, though, I've decided to just uninstall Amarok as there's no point of having it on my system if it always crashes on start-up.

Just as well, for the record, I tried using Clementine instead but it could never get past 77 percent when adding my library. I'm starting to wonder if the reason behind all this is not a software problem, but some possible bad sectors on my HDD. :eek:

For now, it seems, back to the drawing board.

---

### Post by inobe on 2012-01-11
bad sectors would usually slap a startup disk scan in the face..

if you didn't feel any of that booting up, it should be good., linux is really good at throwing warning punches:D

but the upgrade deal should help, just think of it being similar to upgrading a iphone/ android, it just gets better..

---

### Post by iflanery on 2012-01-11
I've realized a new possibility for what's wrong: this could be linked to several of the files *themselves* in my ~/Music directory. I've discovered that many of these files will not play on VLC, either, causing the program to choke until I stop and choose a different file to play.

Not much, but could this be valid?

EDIT: Okay, so it turns out, that it MUST be my laptop HDD. I find it very odd that data that I had sucessfully stored several times between computers would simply refuse to cooperate when placed on my laptop. The kicker was that when performing a routine restart, my laptop simply hung at the boot screen. Rebooting into recovery mode revealed bad sectors on the disc. Sooo... it looks like I'm back to using my aging desktop for the time being. ](*,)

---

