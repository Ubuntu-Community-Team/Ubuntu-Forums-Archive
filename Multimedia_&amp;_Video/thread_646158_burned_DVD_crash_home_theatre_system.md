---
title: "burned DVD crash home theatre system"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by A-dogg on 2007-12-20
Yes -- it's true. Bizarre, but...

I burned some copies of my set of The Wire, season 4 using k9copy to make the .iso. Whenever the burned DVD moves to a new chapter in an episode, the Onkyo DVD player and amp power off and restart.

I've tried burning to Sony DVD+RW and Tayo Yuiden (spelling?) DVD-R discs. I've tried burning the .iso with nautilus, k3b, dvd decrypter (in wine), and nero (in wine).

Same problem everytime. but here's the thing... I tried these discs on a friend's crappy $25 DVD player and they worked fine. 

When I made backups of my Wire, season 3 in XP, they played fine on my Onkyo system. So obviously, Onkyo doesn't like linux-burned discs.

Has anyone heard of this before?

---

### Post by sdowney717 on 2007-12-31
is libdvdread3 installed?

library for reading DVDs
libdvdread provides the functionality that is required to access many DVDs. It
parses IFO files, reads NAV-blocks, and performs CSS authentication and
descrambling.

libdvdread currently uses libdl to dynamically probe for libdvdcss at runtime.
If found, libdvdcss will be used to decrypt sections of the DVD as necessary.

there are some posts where k9copy would play discs in some players and not othere and the posts seem to implicate libdvdcss  libdvdread3 not installed.

you can also try taking the ripped *.iso file made in linux and burning that from windows. This way you could find out if it is the ripping or the burning causing your problem.

---

### Post by mc4man on 2007-12-31
seeing as though you have and are using wine install VobBlanker .
output in k9 to a folder or grab the video_ts from /tmp/kde-<user name>/
Do a mock strip of the video_ts with vobblanker (easiest is to ck. use input folder, make sure you have avail. space). I've noticed that sometimes the output from k9 can use a little correcting though overall had no problems. You can then delete the vobblanker backup , build an iso and burn (try imgburn in wine for build and burn or native apps)

---

### Post by CHFFriday on 2007-12-31
I will try to help you with this.  I will try to explain issue about copying DVD movies using Linux. 

Most of the DVD copy programs/software used with Linux use the libdvdcss2 + libdvdread3 files to decrypt (remove the copy protection etc). The movie companies are way ahead of what libdvdcss2 + libdvdreads3 are capable of doing.

Next, all most everyone copies from DL (double layer) DVD to SL(single layer) DVD SL is half the size as DL so it is necessary to shrink the data to get it on a SL DVD disk.  

The burning process is next.

As you can see it is a very complicated process as it should be as the Movie companies don’t want you to make copies as we all know.

 Most the time in Linux this is done in steps. In Windows all the steps are done at one time. K9Copy attempts to do the same thing as most Windows programs do but does not always work.  I’m hoping Ver 1.2.2 will have all the fixes to make it more reliable. I haven’t tried it yet.

The best Windows programs out there are AnyDVD and DVDFab. AnyDVD will NOT run in Linux. DVDFab will run in Linux using WINE.

Now for the DVD player subject. As you may know DVD players are designed to play movies made for the Region you are in. USA is Region 1. Some DVD players are also made not to play copied movies and can detect when a copied movies is inserted. These DVD players use different ways to not play the DVD. It seams the Onkyo just shuts down. I have seen some players freeze up and you can not get the disk out!  Your friends DVD player most likely is one that will play everything. 

The best Windows programs out there are AnyDVD and DVDFab. AnyDVD will NOT run in Linux. DVDFab will run in Linux using WINE.

mc4man is very good at this subject. Try his sugestions 
!

---

### Post by A-dogg on 2008-01-01
thank you all for your suggestions. 

let me clarify: my onkyo has played every other copied/burned movie i've thrown at it, but for this whole set, it would "reboot" my entire component system. who knows why. i've heard that onkyo is good at amps, but not so good at cd/dvd players...

i bought a $30 philips dvd player at circuit city and it played the dvds the onkyo wouldn't play without a hitch.

so it seems the onkyo is just a substandard peice of equiptment. the $30 single disc cd/dvd player outperforms the $300 cd/dvd carousel player...

generally, I use pinnacle instantcopy to compress my backed up dvds or CloneDVD if I want to keep the menu structure. this is all in windows, mind you. in linux, I've been playing the k9copy and k3b, both sweet programs, as well.

---

