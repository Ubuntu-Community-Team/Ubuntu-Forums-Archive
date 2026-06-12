---
title: "Brasero claims FLAC files are not valid audio files"
date: 2012-01-29
forum: Multimedia Software
---

### Post by jamesisin on 2012-01-29
All of the albums I have ripped recently with Exact Audio Copy are being rejected by Brasero if I attempt to burn a CD using them.  Other files from previous periods (possible using applications other than EAC) Brasero accepts.

These same rejected files are playable in Movie Player, VLC, mouse-over preview, Banshee, and Rhythmbox (on this and other machines).  The permissions all appear to be the same whether burnable or not (r/w, r, r).

I did find one downloaded album which is having the same problem so it's possible that it's merely coincidence that all of my recent rips are not working.  Then again maybe it was ripped on an Ubuntu 10.04 machine using EAC; what do I know?

The error is "[some audio file] could not be opened.  [some audio file] is not suitable for audio or video media."  And yet every other media device I have plays them just fine...

What?  A little help?

---

### Post by wolfen69 on 2012-01-29
You need to burn flac files as data, not audio.

---

### Post by jamesisin on 2012-01-29
I don't want a CD of FLAC files.  I want an audio CD.

Are you suggesting that Brasero won't transcode the files as it burns the CD?  I'm pretty sure it does.  I have burned CD's from my playlists in the past (and my entire collection is FLAC).  As a matter of fact to test this I just burned a CD now from FLAC files by selecting an album of FLAC files (at random) in Banshee and using the Write CD option from the right-click menu with those tracks hi-lighted.  Plays fine in my DVD player.

Regardless this wouldn't explain why Brasero accepts *some* of the FLAC files but not these most recent files ripped with EAC.

---

### Post by wolfen69 on 2012-01-29
Try k3b then. But you will also need libk3b6-extracodecs. I've burned audio cd's before with it.

---

### Post by mc4man on 2012-01-29
you could also just have flac decompress to wav, then burn the .wav's

If so I'd just cd to a dir. holding the .flac's & at that prompt run a simple command

Ex. - create a holding folder named 'burn', then have flac output the .wav's there

```
mkdir burn && for f in *.flac; do flac -d --output-prefix=./burn/ "$f"; done 
```

You could run a problem .flac thru flac  using -V option to see if anything shows or maybe -a on one that doesn't work & one that does to look for diff's that may be causing this

---

### Post by jamesisin on 2012-01-29
I thought maybe there was something Brasero found unpleasant in the meta-data, so I went in and changed the tags on two albums (added disc number 01) to see if that act of saving them would correct anything.  No such luck.

K3B was able to burn the playlist without difficulty and that CD plays fine in my DVD player.

Here is the thing though: my question isn't how do I burn these songs; my question is how do I make Brasero do what it's supposed to do?

I advocate for Ubuntu (and Linux in general) so having things at this basic level function is vital.  Brasero, the default burning tool and the tool called up by the now default media library application (Banshee) and the most common media library application (Rhythmbox), should be able to burn discs from FLAC files ripped through the de facto error correcting ripping software (EAC).

It is very important to me that I find a solution and not just a cumbersome workaround (export to playlist file, import to an application that must first be installed, and finally burn the CD).

So, back to my original question: what is/not Brasero or EAC doing (and how can I fix it)?

Test Results:

The problem files give this error when running flac -V against them.

```
ERROR: input file /path/to/file.flac has an ID3v2 tag
```

---

### Post by mc4man on 2012-01-30
Opps- wrong option, that would be -t (for test) though likely will come up good

Anyway did you or whoever use eac in wine or windows? (I could run a cd or 2 later this week with eac in wine to see if brasero dislikes

---

### Post by MoreOrLess on 2012-01-30
It could be this bug: [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/504645](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/504645)

---

### Post by mc4man on 2012-01-30
> **MoreOrLess said:**
> It could be this bug: [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/504645](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/504645)
That sounds just like it & what's interesting there is that the attached flac was also created in eac

---

### Post by jamesisin on 2012-01-30
Yeah, -t came up "OK".

I added my information to that bug report and linked it back here.

Thanks for finding it.

---

### Post by mc4man on 2012-01-30
Added eac & tried a few things. Initially couldn't get freedb going, seemed to keep failing on a server error, site down for maintenance. Anyway added a wine registry key to use musicbrainz instead for the moment so could proceed

The flac attached to the bug report had ID3 tags, see screen 1, brasero refused it

Ripped a track in eac without enabling adding ID3 tags, screen 2, brasero accepted it fine

Then enabled ID3 (EAC > compression options > Add ID3 tag , screen 3, very similar to the bug flac, brasero refused 

So maybe ck. to see id ID3 tags are present, mediainfo will show in HTML view or open in hex editor

---

### Post by shantiq on 2012-01-31
here useful adjunct info for guys who use [**EAC**]("http://www.hqshare.net/showthread.php?t=931") and want to maximize results


also [**lossless**]("http://www.hqshare.net/showthread.php?t=51265") settings

---

