---
title: "What format DVD?"
date: 2011-12-06
forum: Multimedia Software
---

### Post by arst06d on 2011-12-06
I have downloaded several movies from the interweb and am burning to dvd.

I have a multi-format dvd burner and have had no problems burning DVD+R or DVD-R and they all play OK on my Yamada DVD player.

I just tried burning a longer movie and used a DVD+R Dual Layer for this - but the Yamada player says No Disc ie it's not recognising it.  Now I'm wondering if this is just the +R Dual Layer format it doesn't like or whether it will be the same for -R DL too?

Strangely enough I have a copy of the Lord of the Rings which is over 200 minutes each film, and using K3B I can see that the media is Dual Layer - but not what format.

Anyone know what format commercial releases are burned to, or how I can find out what the media format is on the LoTR discs?

If it matters, my cd player is a Yamada DVDSlim 5520.  I know it's pretty old, but it works and obviously plays recent releases.

I'm using 11.10 and k3b which gives the following info about the LoTR disc:

Medium

Type:	DVD-ROM
Media ID:	unknown
Capacity:	770:05:22 min (6.6 GiB)
Used Capacity:	770:05:22 min (6.6 GiB)
Remaining:	00:00:00 min (0 B)
Rewritable:	no
Appendable:	no
Empty:	no
Layers:	2
Sessions:	1
ISO9660 Filesystem Info

System Id:	-
Volume Id:	LOTR_THE_FELLOWSHIP_OF_THE_RING
Volume Set Id:	UNDEFINED
Publisher Id:	-
Preparer Id:	-
Application Id:	-
Volume Size:	6.6 GiB (2,048 B * 3,465,397 blocks = 7,097,133,056 B)
Tracks

Type	Attributes	First-Last Sector	Length
1	(Data)	no copy/uninterrupted	0 - 3465396	3465397 (770:05:22)

I could go and buy a DVD-R DL disc to try, but I thought I'd throw it open first of all.

Appreciate any help.

---

### Post by gordintoronto on 2011-12-06
You didn't say that your player can play the Lord Of The Rings disc, but I assume that it can?

This page: [http://computershopper.com.com/dvd-players/yamada-dvdslim-5520-dvd/1707-6473_7-32546304.html](http://computershopper.com.com/dvd-players/yamada-dvdslim-5520-dvd/1707-6473_7-32546304.html)
doesn't list DL as a supported format.

Can you play the DL disc you burned, on your computer?

Are you actually burning DVDs, or just copying the downloaded files to the discs? For example, the program DeVeDe will take video files and create an ISO in real DVD format. Open any commercial DVD in your file manager to see what I mean. Most people would say the format of a DVD is ISO9660.

---

### Post by arst06d on 2011-12-06
Hi and thanks for the response

Yes, my Yamada DVD player will play the LoTR discs no problem, and that's part of my confusion with this - why will it play commercial DL discs but not DL discs I have burned.

I am actually burning the .iso to dvd, not just copying it to the disc.  If the stuff I have is the actual disc content eg the video_ts files then that's different - they can just be burned as they are.  Done both successfully many times on single layer discs which play fine on the Yamada.

The DL disc I created will play OK on my pc.

I would say that it's a limitation in the Yamada except for the fact that it's playing commercial DL discs like LoTR. :confused:

---

### Post by gordintoronto on 2011-12-06
It sounds like you know what you are doing. A lot of people don't.

This is a puzzle. Not having your DVD player, I don't think I can help. Good luck!

---

### Post by arst06d on 2011-12-07
Thanks for your time anyway.  I've been looking at new dvd players on various web sites and they don't specify whether they play DVD+/-R DL discs, so who's to know?

---

### Post by enjoijesus94 on 2011-12-07
probaly your dvd player my friend 
iv got a iomega DVD-R DL
on my laptop with no problems 

if you need any help just post:popcorn:

Cheers

---

### Post by ed bear on 2012-04-05
I can clear up something that confuses a lot of folks...

ALL DVD-ROM drives can read and play dual-layer DVDs; this is the original spec used for all commercial DVD releases (except for a very few which are short enough to fit on a single-layer disk).

On the other hand, while you can get drives that will WRITE:

DVD-R     DVD+R     DVD-RW     DVD-RW

and some other variants like DVD-VR, DVD-RAM and the like, there are almost no drives out there that can WRITE Dual Layer disks!

The dual-layer formats I know a bit about are:

DVD-R 2L    DVD+R 2L     DVD-RW 2L   DVD+RW 2L

Some manufacturers use the suffix "DL" instead of "2L."

Thus - listen up, everyone - being able to read dual-layer disks in a drive does NOT mean you will be able to write them!  You need both a 2L drive AND 2L disks (neither of which are large-volume or cheap) to write them.

[NOTE: Packages containing 2L blanks warn you to upgrade drive firmware before trying to burn DVD 2L disks.  I don't know if this is because many were problematic or if the upgrades contain more DRM.]

It was intended when DVDs were designed that everyone would be able to read them, and write them, but that people would not be able to copy commercial DVDs onto the smaller disks in full quality.

That's why there are programs like DVDSHRINK out there.  And why people will remove "extras" from DVD titles to reduce quality degradation.  They don't make it easy.

I did once try to figure out DVD9to5 for someone... not easy: I managed to get it to shrink files but only one track at a time, and found no what to put them into a single DVD or image.  (If there's a thread on using it, I'd like to hear about it.)

There's also XDVDSHRINK, but I have no idea of how to install it.

Anyway, if you want to save a single data file larger than 4.3GB, you have to go 2L sooner or later.

I found a 2L drive in a discarded hand-me-down machine last week, and have been trying to learn to use it in 2L mode.  No luck so far...

My drive is an LG H54N, and I bought some Sony blanks, in a blue 2-pack rated at 8.5GB and 2.4-8x speed.  They are clearly labeled DVD+R 2L (as is my drive) though for some reason an "RW" logo also appears on the box.

My system is a fully updated (to 2.6.24-31 level at the moment) Hardy Heron 10.4, and Brasero has been been happily reading and writing CD, CD-R, DVD-ROM, DVD+R and DVD-RW disks with impunity on a P4-2.2GHz with 750MB RAM.  I've used an ASUS drive until now, but have successfully burned a DVD+R on the first try with the new LG.

My first attempts to burn a DVD+R 2L disk, though, ended with a complaint from Basero in the pre-burn dialog box that "The medium is not writable with the current set of plug-ins."

This happens whenever a 2L disk is in the drive.  It isn't a video file problem, since it won't let me burn even a single little text file.  Won't even let me get to the point of selecting a SIMULATED burn!

I will keep trying, but toss this in here in case anyone knows the answers.  Brasero shows three installed plug-ins:

local-track     md5sum     md5sum-file

But Sunaptic and Brasero tell me nothing about how to get other plug-ins.  I've been reading threads all night, and there are people who are cheerfully making2L disks with Brasero, so I'm still looking.
ED BEAR
):P

---

