---
title: "Difficulty playing DVDs"
date: 2009-09-12
forum: Mythbuntu
---

### Post by sschneidertx on 2009-09-12
I am having difficulty playing many DVDs.  Some of them just stop at the "FBI" warning screen and never progress.  Others just stop on a blank screen and never start playing.  I am running Mythbuntu 8.10 and I have the most recent updates loaded.  Some DVDs play just fine.  It appears that the Disney DVDs cause the most problems.  Currently trying to play Mulan and I can only get to the FBI Warning page.

---

### Post by tudor117 on 2009-09-12
What player are you using?
Are you saying you have a problem playing[COLOR=RoyalBlue][ _Encrypted DVDS_]("https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs")[/COLOR]?
Enable medibuntu and follow the instructions from their website.

---

### Post by sschneidertx on 2009-09-12
I am able to play many Disney and other encrypted DVDs.  I am jsut having a sporadic problem with a few of them and other DVDs.  I do not think it is an encryption issue as I have installed the non-free encoders and libdvdcss2.  Any other ideas why a DVD would hang before the main menu?

---

### Post by klc5555 on 2009-09-12
> **sschneidertx said:**
> I am having difficulty playing many DVDs.  Some of them just stop at the "FBI" warning screen and never progress.  Others just stop on a blank screen and never start playing.  I am running Mythbuntu 8.10 and I have the most recent updates loaded.  Some DVDs play just fine.  It appears that the Disney DVDs cause the most problems.  Currently trying to play Mulan and I can only get to the FBI Warning page.

The newer Disney DVDs pose special problems in a number of ways because of their new DRM setup (as do Sony discs).

They're generally too much for the internal myth player to handle. About the only Linux player that can deal with them is VLC. (The older VLC version 0.8xx is better than the newer 0.9xx found in Ubuntu 9.04, and is evidently the only tool that can reliably rip one of these Disney discs) Even here the process is not completely seamless. In VLC when the one of the fatal sequences come up (like the FBI screen), if you right-click on the screen, go to the video menu and click on the "disable video trac" the video should skip over the sequence and continue on to the main movie.

---

### Post by movieman on 2009-09-13
> **klc5555 said:**
> The newer Disney DVDs pose special problems in a number of ways because of their new DRM setup (as do Sony discs).

Yeah, Disney seem to have decided that they don't want Linux users buying their DVDs. Which is fine by me, I'm glad to support them in their quest to avoid taking my money.

The stupid thing is that from what I understand you can easily rip the movies from the disks despite their DRM crap, you just can't watch the DVD.

---

### Post by kroneaux on 2010-03-19
I used vlc to play Disney's Up (Rental version) which works great. Totem and Mplayer would not work. Vlc told me Title 50 was the movie. If I open title 50 with dvd no menu option all 2g of memory gets used faster than I can shut down the player. I have tried some other dvd software and this memory leak happens also. I am running Hardy but have had similar memory problems with fedora 12 and this dvd (4g out of 6g gets used). When all memory gets used the system freezes. So, has disney found a way to take down linux machines? Is this a security issue? Memory management issue? Or a problem with linux handling broken or "fixed" dvds? Makes me wonder what kind of voodoo they could throw at windows.

---

### Post by klc5555 on 2010-03-19
> **kroneaux said:**
> I used vlc to play Disney's Up (Rental version) which works great. Totem and Mplayer would not work. Vlc told me Title 50 was the movie. If I open title 50 with dvd no menu option all 2g of memory gets used faster than I can shut down the player. I have tried some other dvd software and this memory leak happens also. I am running Hardy but have had similar memory problems with fedora 12 and this dvd (4g out of 6g gets used). When all memory gets used the system freezes. So, has disney found a way to take down linux machines? Is this a security issue? Memory management issue? Or a problem with linux handling broken or "fixed" dvds? Makes me wonder what kind of voodoo they could throw at windows.

I've not seen this activity when using VLC. However, I can't ever get Disney DVDs to actually _play_ in Linux, so to play them I have to do a VLC rip and then frame index the resulting file with mythtranscode. This will play perfectly, but subtitles (if any) are a problem.

Anyway, after such a rip and transcode, I would frequently find the machine unresponsive. After ssh-ing and running "top" I found that mtd (of all things) was leaking memory after this process. I don't know why, after just running mythtranscode to build an index, but killing and restarting mtd would quickly return things to normal.

You might want to set up a play while ssh-ed into the machine, and use something like "top" to see what precise process is sucking up all the oxygen. It may be not be the player itself; it might be something that you can live without for the duration of the play, and then restart.

---

### Post by johnnysako on 2010-04-04
I am also finding that upon inserting some disks (mostly Disney/Pixar) into my recently upgraded Lucid machine that mtd will start and suck up all the memory making the whole system terribly unresponsive.  Killing the mtd process returns things to normal.  This seems to happen regardless of attempting to watch the disk.

---

