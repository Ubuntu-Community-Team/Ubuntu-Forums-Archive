---
title: "How to create an audio CD?"
date: 2013-07-14
forum: Multimedia Software
---

### Post by pastim on 2013-07-14
I am on ubuntu 12.04, 64 bit.

I want to create an audio CD from a set of tracks I have recorded.  They are 16 bit flacs, with title and artist information embedded.

With brasero as soon as I hit 'burn' it ejects the blank CD-R and gives a gstreamer error.

With k3b I can create an audio CD - Great!  The only problem is that it shows my titles etc before writing, and then blanks them out when it writes the CD.  I have tried to mislead it by giving an incorrect url for freedb, but as far as I can tell it insists on using the cddb mechanism to overwrite my carefully crafted titles.

I found a way to install gnomebaker.  When I select an audio project it cannot see flac files, only mp3s.  The flac library is installed (1.2.1-6), as is libflac8 and libflac++6.  The gstreamer ffmeg library is also installed (gstreamer0.10-ffmpeg 0.10.13-1).

I also tried DeVeDe but that only does video.

Help!

---

### Post by pastim on 2013-07-14
Having tried many things it now seems that Brasero can write wavs, but not flacs.  This looks like some form of incompatibility between Brasero and gstreamer on ubuntu 64 bit 12.04.

I struggled to find a way of proving or disproving whether CD text had been written, since my normal CD player doesn't seem to show it, and it seems few ubuntu audio CD players do either.  I eventually found a way, installing libcdio-utils and running cd-info -C /dev/....  Rhythmbox sometimes shows the text and sometimes not.

Brasero, when using wavs, does write cd text that can also be viewed using Rhythmbox.  K3b may have been writing CD text, according to cd-info, but Rhythmbox can't see it.

So I can either convert my flacs to wavs and use Brasero, or use K3b if I am not concerned about CD text.

---

### Post by Cheesemill on 2013-07-15
Try using [xfburn]("apt://xfburn") instead. I've always used it to create audio CD's from my FLAC's and I've never had any issues.

---

### Post by VanillaMozilla on 2013-07-15
K3b.  The file name is not the same as the track title.  As far as I know you have to enter the title manually.  Right click, select Properties, I think.  Or try double clicking I think.

Oh, wait, I see that you have entered titles.  I suppose you could defeat CDDB by disconnecting from the Internet momentarily.  Are you sure you're using this for legal purposes?

---

### Post by pastim on 2013-07-15
> **VanillaMozilla said:**
> Oh, wait, I see that you have entered titles.  I suppose you could defeat CDDB by disconnecting from the Internet momentarily.  Are you sure you're using this for legal purposes?
Since this is stuff I created and recorded myself it's completely legal, and there's no way CDDB could ever know what it was.  

As to the CD Text, I was wrong in believing that the data had been lost by K3b.  It seems that there's more than one way to store the text, and K3b maybe does it one way, other software does it another way, and some players only see some methods. See [https://en.wikipedia.org/wiki/CD-Text](https://en.wikipedia.org/wiki/CD-Text).  

Wonderful things standards....

---

### Post by VanillaMozilla on 2013-07-16
OK, I don't know what the problem is.  I do exactly the same thing all the time.  While random, strange CDDB entries do show up from time to time, I don't remember them ever getting in the way or overwriting data I had ever entered.  I don't even remember if this happens on K3b or on some other program, but I don't remember ever having a problem with K3b.

I just checked.  .Wav files are usually entered with blank title, since the metadata are not(?) imported.  Flac and mp3 files have the track name used as the title, but I can change it.

I've never had a problem with titles not showing up correctly on the CD, as far as I know (although I often don't use that feature).  In other words, no problem here, for what it's worth.

I agree, computer standards are a mess.  Isn't it nice that we have so many of them?

---

