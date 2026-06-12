---
title: "CD Ripper with MP3 &amp; CDDB support"
date: 2011-10-14
forum: Multimedia Software
---

### Post by Amon_Re on 2011-10-14
As you all probably know there is some serious issue with Sound-Juicer, Banshee & Rhythmbox when it comes to ripping CD's.

Ever since Musicbrainz switched their back-end months ago these 3 haven't been able to fetch CD tracks from it.

I've patiently waited a while now for the release of 11.10 and that **** **still** isn't fixed, I have a ton of CD's to rip so I'm looking for alternatives, does anyone, anywhere have an idea what I can use?!

---

### Post by BicyclerBoy on 2011-10-14
abcde

This is a terminal script/program that uses cdparanoia etc..
Needs a bit of config first to get the output file format/quality etc.

But works very well.

---

### Post by Amon_Re on 2011-10-14
I'm reverting to good old GRIP

---

### Post by beew on 2011-10-15
According to the links below the problem has been fixed for sound juicer and Banshee if you install from ppas.

[http://tickets.musicbrainz.org/browse/MBS-2249](http://tickets.musicbrainz.org/browse/MBS-2249)  (see second last post)

[http://askubuntu.com/questions/43905/banshee-is-unable-to-determine-audio-cd-metadata](http://askubuntu.com/questions/43905/banshee-is-unable-to-determine-audio-cd-metadata)

---

### Post by andrew.46 on 2011-10-15
> **BicyclerBoy said:**
> abcde

This is a terminal script/program that uses cdparanoia etc..
Needs a bit of config first to get the output file format/quality etc.

There is a sample configuration here for abcde and mp3:

[http://www.andrews-corner.org/abcde.html#mp3](http://www.andrews-corner.org/abcde.html#mp3)

---

### Post by DJonsson2008 on 2011-11-20
according to [http://ubuntuforums.org/showthread.php?t=1763064&page=2](http://ubuntuforums.org/showthread.php?t=1763064&page=2)

One needs to add the following to the repository for Natty 

deb [http://ppa.launchpad.net/phw/musicbrainz/ubuntu](http://ppa.launchpad.net/phw/musicbrainz/ubuntu) natty main 
deb-src [http://ppa.launchpad.net/phw/musicbrainz/ubuntu](http://ppa.launchpad.net/phw/musicbrainz/ubuntu) natty main 


When I do this on my Natty 11.04 it has no effect on on Sound Juicer. 


1. Is repairing the Musicbrainz/Sound Juicer problem possible on.
   _Natty 11.04?
   _Natty 11.10?
   _Hardy?
  

2. Why doesn't; adding the above repositories and reinstalling 
   Sound Juicer not work on a Natty 11.04 instance?
   _Is there something to the procedure I'm missing?

---

