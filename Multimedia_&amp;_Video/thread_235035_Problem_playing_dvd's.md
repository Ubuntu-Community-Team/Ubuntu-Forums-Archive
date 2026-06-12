---
title: "Problem playing dvd's"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by gargoyle on 2006-08-12
I am trying to play dvd's but I seem to have a problem.
I have downloaded and installed the needed files for this from
[Playing encrypted DVDs]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9")
I have verified through Synaptic they are installed.

However when I start Totem and click on Movie and select
Play dvd
it gives me a error
[B]Totem was not able to play this disc.
Failed to mount /dev/hdc[/B]

What seem to be the problem here?

I know the drive is working because if I place a data disk in there it will open it up. So why won't it open the dvd?

---

### Post by szadek on 2006-08-12
> **gargoyle said:**
> I am trying to play dvd's but I seem to have a problem.
I have downloaded and installed the needed files for this from
[Playing encrypted DVDs]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9")
I have verified through Synaptic they are installed.

However when I start Totem and click on Movie and select
Play dvd
it gives me a error
[B]Totem was not able to play this disc.
Failed to mount /dev/hdc[/B]

What seem to be the problem here?

I know the drive is working because if I place a data disk in there it will open it up. So why won't it open the dvd?
Probably Totem, which is, for me, by far, the worse media player I've seen to date.  It **may** be able to play 1 in 100 media files, and that is on a prayer.    I've updated it as much as I know how, with directions from the forums etc, and it does not work.  I suggest getting MPlayer.  I've got that to work on a bit better scale.

---

### Post by gargoyle on 2006-08-12
I did a search through Synaptic but did not find any Mplayer.
Is there a different name for it?
Any reason it might be listed under Synaptic?
I new at this and do not fully understand other ways of installing thing but Synaptic. So if you are going to suggest another method, be aware I will need some detail instruction.  Also I would like to know what I am doing and why not just a bunch of instructions.
OK
Doing a google search I find it for Breezy but not for Dapper.
Would the Breezy version work?

Any help here?

---

### Post by thistlebrae on 2006-08-12
Anxious to follow the feedback on how to get Mplayer...

---

### Post by gargoyle on 2006-08-12
Well it seems like I was chasing a ghost.
I used automatix to down load and install Mplayer.
Guess what it did not work, it could not find the media (DVD).

I then thought to check out the dvd rom under Winxp. It could not play dvd either.  It seem the the dvd drive had died in between the last time I used it and the installation of Ubuntu. So I swap the drive for another and sure enough everything works.

So totem may not have been the problem but a bad piece of hardware.
One more problem solve and on my way to full time use of Ubuntu.

Thank for the replies.

---

### Post by thistlebrae on 2006-08-13
Gargoyle,

Glad to hear you finally got it running.  Oddly enough, it was a similar hardware problem that caused me difficulty in loading Ubuntu in the first place.  My CD-R/W turned out to be the proble in endless "corruption errors"

I unplugged it swapped it out for the DVD above and the install then worked like magic!.

Now...back to the DVD issue.  I got Totem to work by removing plain Totem and replacing with Totem-Xine.  The only problem is that I cannot eject once I stop or finish watching the movie (and once it starts playing the DVD drive disappears from the drive list under Places|Computer).  The only solution I have found for this is to Logoff and then back on.  Once I do that the drive is released, reappears on the list and then I can eject the disc.  A bit of a pain..yes...but better than no DVD.  

If I ever find the solution I will bring it back here.

---

