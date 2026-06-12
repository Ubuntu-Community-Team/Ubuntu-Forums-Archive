---
title: "Question about ripping music CD's in Ubuntu 8.10"
date: 2008-11-30
forum: Multimedia Software
---

### Post by VuzeLover on 2008-11-30
Took me a while to figure out how to rip a music CD in 8.10.  Now I see that you use Rhythmbox.  My question is, how do you get Rhythmbox to auto rip music CD's when you insert them into the disc drive.  Also does the Rhythmbox ripping do any error correction?  I would not mind any suggestions for ripping music CD's.  The main thing is that I have hundreds of CD's and some of them are scratched.

---

### Post by mc4man on 2008-11-30
I don't believe rhymthbox can auto do anything.
Rubyripper does use cdparnanoia for error cor. and can be setup to auto run.

Basically you'd just insert the cd and it would rip, or rip and encode in the background. (insert cd and walk away if desired

Or if you wanted to watch, with a slight change it will autostart and you'd just have to click the rip button.

I don't use 8.10 but I know from testing it that the very latest version will run on 8.10 though the gui is a little messed up.

I would have to test it first to see if things worked out. (it works perfectly on 8.04. (hint

What are you ripping to?

If it's just to .wav I've noticed that rythmbox in 8.10 has a problem with .wav's not ripped with gstreamer apps or by itself.

To test on your box take a .wav ripped elsewhere or browse an audio cd, drag a track to your desktop and see if rhythmbox can play it after it's been copied.

RR will leave a log in each albums folder so even if you let it work in the background you can always review

> This log is created by Rubyripper, version 0.5.4
Website: [http://code.google.com/p/rubyripper](http://code.google.com/p/rubyripper)

Cdrom player used to rip:
ATAPI DVD A  DH20A4P 9P59
Cdrom offset used: 0

Ripper used: cdparanoia 
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-other	-> neroAacEnc -q 0.61  -if %i -of "%o.m4a"

CDDB INFO

Artist	= Quicksilver Messenger Service
Album	= Happy Trails
Year	= 0
Genre	= Rock
Tracks	= 10

01 - Who Do You Love (Part 1)
02 - When You Love
03 - Where You Love
04 - How You Love
05 - Which Do You Love
06 - Who Do You Love (Part 2)
07 - Mona
08 - Maiden Of The Cancer Moon
09 - Calvary
10 - Happy Trails

STATUS

Starting to rip track 1, trial #1
Starting to rip track 1, trial #2
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: df669cd908e329d42c9c49c746256774

Starting to rip track 2, trial #1
Starting to rip track 2, trial #2
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 0396da9265d88844db6c8152ca270eee
...........ect.

---

### Post by VuzeLover on 2008-11-30
> **mc4man said:**
> I don't believe rhymthbox can auto do anything.
Rubyripper does use cdparnanoia for error cor. and can be setup to auto run.

Basically you'd just insert the cd and it would rip, or rip and encode in the background. (insert cd and walk away if desired

Or if you wanted to watch, with a slight change it will autostart and you'd just have to click the rip button.

I don't use 8.10 but I know from testing it that the very latest version will run on 8.10 though the gui is a little messed up.

I would have to test it first to see if things worked out. (it works perfectly on 8.04. (hint

What are you ripping to?

If it's just to .wav I've noticed that rythmbox in 8.10 has a problem with .wav's not ripped with gstreamer apps or by itself.

To test on your box take a .wav ripped elsewhere or browse an audio cd, drag a track to your desktop and see if rhythmbox can play it after it's been copied.

RR will leave a log in each albums folder so even if you let it work in the background you can always review

Thanks I will look into Rubyripper.  I am ripping directly into flac.

---

