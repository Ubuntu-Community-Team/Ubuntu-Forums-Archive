---
title: "No audio in recordings if using RTjpeg but MPEG4 works fine"
date: 2010-01-28
forum: Mythbuntu
---

### Post by go2dell on 2010-01-28
Let me preface this by saying that I haven't had occasion to touch MythTV in several years, so this is really my first go around with Mythbuntu, and so far it's pretty darn slick.  Even with my ancient, oddball hardware, it's been fairly easy to set everything up.

Now for my problem.  After driving myself crazy with muting and unmuting various inputs from the sound card, I've discovered that I can stream recordings to VLC and have sound *only* if I encode everything in MPEG4.  RTjpeg offers only silence.

Oddly enough, RTjpeg does provide audio when watching live, but I suspect the analog audio from my TV card is just bypassing the encoding process and coming directly out of my sound card.

I discovered the solution(?) to my problem when I finally remembered that, "hey! There should be log files on this thing!" #-o  The helpful little log file told me that /dev/video0 is an Unknown video codec, and I should set up my Software Encoders.  It "assumed" RTjpeg, and we all know the problem with assuming anything.

Some background:  I have an ancient PC that I want to use as a backend-only machine, and I plan to watch anything it records by streaming directly from MythWeb.  Except for the audio problem, this appears to work fine.  The cable connection I'm using this on has absolutely horrible quality, but it's a private system so there's nobody that cares to do anything if I complain.  Therefore, I don't really worry that much about missed recordings, and the box thats holding Mythbuntu was free, so I want to put it to good use.

Right now this is still a test build.  I will be adding a second drive for recordings before I put the box into production, plus I've goofed around with so many settings that it's difficult to remember what I did.  Therefore, I have no problem with tearing this thing to bits if that's what I need to do.  I'm still in the "having fun" stage; the "grrr, why did it stop working?" stage will come after the final build.  :D

About the hardware:
Mythbuntu 9.10
Video card: Prolink PixelView PlayTV Pro Ultra (PV-304+ / cx8800)
Sound card: Turtle Beach Santa Cruz (CS4630-CM / snd_cs46xx)
Box: Dell Dimension XPS B1000 / P3 / 1GHz / 256MB RDRAM (yes, really)

You can see that the box is basically underpowered for any sort of real usage, but it works great as a little home server or web server.  It doesn't really have enough oomph to run a full front end/back end setup, so that's why I decided to try just streaming to watch on my other machines.  I just wanted to give it a use that would be of more value to me and show it that it's still loved. :redface:

So now:
[LIST]
[*]Does anybody know why MPEG4 has audio but RTjpeg doesn't?
[*]Is there any particularly good reason I should want to use RTjpeg instead of MPEG4?
[*]Is there a magic combination of devices to unmute in ALSA if I want to use RTjpeg?
[/LIST]

TIA!

---

### Post by go2dell on 2010-02-10
The solution to my problem was that audio needed to be set at 44100 in all my recording profiles.  Now I can use RTjpeg just fine.

---

