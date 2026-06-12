---
title: "DVD regions codes - why doesn't ubuntu seem to care about them?"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by sparky06 on 2006-08-15
Hi all,

I just got DVD playback to work on my ubuntu/win xp dual boot laptop.

One thing that's got me stumped is that ubuntu doesn't seem to care what the region code of the disc is - I can happily play all my region 1 and 2 DVDs.

However in Windows XP I can only play region 2 DVDs (or change the region code of the DVD player - which can only be done 5 times).

Obviously I'm pretty happy about this, but does anyone know why this is?

---

### Post by finite9 on 2006-08-17
that is weird, because although Linux software may disregard region codes, your dvd drive should not - unless you have already flashed your dvd drive with a firmware that is region free.  Otherwise, you bought a dvd drive that was already region free.  Normally, all drives have a region set when bought and you have 5 chances to change it.

It's not strange that Linux software ignores region codes, because most players (if not all) for Linux are considered illegal due to the fact that they use DeCSS in most cases to be able to play DVD's as Linux is free software and no-one thinks they should have to pay royalties for the ability to play a DVD.  In this context, why would we bother with region codes if simply playing *any* DVD is considered illegal :)

---

### Post by sparky06 on 2006-08-18
That's what I understood - that it was the firmware in the DVD player that determined the region code. I haven't flashed the firmware (too scared!) and WinXP complains and asks if I want to change the region code when I put a region 1 disc into the player.

Is it at all possible that linux can somehow cirumvent the region code stuff in the firmware? Perhaps I might try and find some more DVDs to see if I can reliably reproduce this (I only have a couple of region 1 discs that were bought in error).

I see your point about why linux doesn't care about region codes - it's always  seemed crazy to me that I have to break the law just to watch something I've bought!

---

### Post by finite9 on 2006-08-18
I have some region 1 DVDs and my drive is definitely region 2, but I have never tried to play the region 1's--i'll give it a try tonight and let you know if they worked (I use Totem-xine as it "does" DVD menus but I can try VLC without menus as well).

---

### Post by Lord Illidan on 2006-08-18
Try and use VLC on Windows.

If you use propietary dvd players on windows, they will probably be region specific. I experienced this prob in Windows, until I got VLC...then I could play whatever I wanted.

---

### Post by finite9 on 2006-08-18
well, I have dual boot with Windows XP and I use only VLC in windows for all media.  I have not tried playing both reg. 1 & 2 in Windows with VLC, but I can try this as well.

---

### Post by Lord Illidan on 2006-08-18
Since VLC uses DeCSS you can view all regions..

DeCSS is a marvellous piece of software..it frees me to watch whatever DVDs I want from whatever region I want.

---

### Post by finite9 on 2006-08-19
Well, I think you are plain wrong about the DVD region code thing.  Somehow you mistakenly believe that you can play any region DVD on all DVD drives under Windows with VLC.  This is not true in Windows.

I have VLC 0.8.4a on Windows XP.  When I try to play Gladiator R1 with or without DVD menus then it refuses to play but I get no error message.  Playing a R2 (The Big Blue) works perfectly.  If I try to play R1 in Windows Media Player it pops up a window saying my drive is region 2 and that I need to change it.

I strongly suspect that the same is tru of Ubuntu, as there are several links about region coding in the wiki documentation.  

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

I suspect you have region free drives and are unaware of it, or that there is something specific about your system that enables you to watch both regions, but believe me, it is not true for *all* Windows VLC users...the great majority will probably have region lock in.  I have not yet tested on Ubuntu - will do so later today.

As far as I am aware, region coding is set only in the physical drive and the media software just checks the disc against the drive to see if it's able to play.  As VLC uses DeCSS, it may ignore this check in Linux.  You can 'apt-get install regionset' to check what region your drive is set to.

---

### Post by finite9 on 2006-08-19
Ahhh...from that link:

"[WWW] The author of regionset writes: "On delivery, most DVD drives have no region code set. The drive firmware allows you to change the region code, but on nearly all drives you are limited to five (5) changes. After the fifth change, the DVD drive will stay fixed on that code -- on some drives you can upgrade the drive firmware and have then additional five changes, on other drives you won't be able to change the region code any more."

Maybe this means that if you buy a new drive and there is no region set yet, and you never change/set it in windows, but immediately start using Ubuntu/Linux with VLC, and where VLC doesn't bother with the check, then the drive will never have a region set!  Could this be the reason?  Im just guessing.

Maybe its the media app that detects the first time you play a DVD that there is no region set, and sets it for you.

---

### Post by finite9 on 2006-08-19
I checked this on Ubuntu now and R1 discs do not play in Totem-xine or VLC.  Totem gives error about disc being encrypted and VLC simply does nothing.  R2 disc works fine.  I am going with my earlier idea that you bought a PC and have never run Windows/never set the region code through software on the drive, and as Linux media apps dont check the region code, its not an issue for you.

---

