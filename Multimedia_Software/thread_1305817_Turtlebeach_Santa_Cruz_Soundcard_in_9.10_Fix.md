---
title: "Turtlebeach Santa Cruz Soundcard in 9.10 Fix"
date: 2009-10-30
forum: Multimedia Software
---

### Post by snerd on 2009-10-30
I've got an older TurtleBeach Santa Cruz soundcard that buzzed and crackled really bad in Karmic Koala 9.10 betas, rc's and the final release. A quick fix was to go to preferences, sound, and on the Hardware tab I changed the profile to Analog Surround 4.0 Output. Maybe this will help someone else.

---

### Post by Roel Verlaek on 2009-11-01
Hi there,
I also have an older Turtle Beach soundcard installed on a Dell Dimension 8200 (CPU 2.4Ghz, 1Gb MEM) and experiencing the same problems. However the solution above doesn helpt me at all. I tried al settings but nothing helped.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]  Under Ubuntu 9.04 everything work fine.
Does anybody has a solution for this problem?
Thanks

---

### Post by sweener on 2009-11-18
Same problem here with the buzzing using Turtle Beach Santa Cruz pci card. Did a fresh install of 9.10. Works fine in 9.04. snerd's suggestion did not help.

---

### Post by manco on 2009-12-22
> **snerd said:**
> I've got an older TurtleBeach Santa Cruz soundcard that buzzed and crackled really bad in Karmic Koala 9.10 betas, rc's and the final release. A quick fix was to go to preferences, sound, and on the Hardware tab I changed the profile to Analog Surround 4.0 Output. Maybe this will help someone else.
Worked like a charm!

I just installed 9.10 and was worrying that I wouldn't be able to get the sound card working!

Thanks a million!

---

### Post by BryanPearson on 2010-01-09
For me, Analog 5.0 Surround Output seemed to work best, though I do have a bit of noise now and then.  I tried Analog Mono Output for a while with ZERO noise, ever, but didn't want to do without stereo.

---

### Post by BryanPearson on 2010-01-10
Boy, I posted too fast.  Everything is fine until I adjust the volume.  I can't pick a specific volume.  If I adjust it up or down it will be fine.  But in the transition, it is just noise.  I used to love these cards for Windows gaming, much better use of system resources than the SBlive cards.  But now it seems I will have to find a card suitable for Ubuntu.

[UPDATE]
Tried alsamixer for volume control, and it doesn't cause the problem at all.  Only the GUI volume control causes the problem.  I don't know enough about Ubuntu to guess why this is so, but it does give hope to those users of the CS46xx driver - especially in laptops.

---

### Post by def_mornahan on 2010-02-19
I have been having similar problems with my Turtle Beach Santa Cruz soundcard on a Dell Dimension 8200, running Karmic, and the fix suggested here did not work for me either.  I use Audacious, and while playing back mp3s I noticed two different symptoms:  First, when changing from one track to the next, there was maybe a 50/50 shot, maybe less than that, of having any sound; otherwise it went mute.  If I stopped the track and restarted it, usually a few times, the sound would eventually come back.  Second, whenever something happened in the background, possibly starting a new application or definitely whenever I got new mail, there was a substantial chance of the sound going berserk and blaring this nasty buzz.  It seemed related in pitch the last sound being played.  This I fixed by changing the volume control many times, up or down at random.  Stopping the track would not work with the second problem, and changing the volume would not work with the first (I think).

Apparently this is [bug 428619]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428619").  Somewhat educational, if depressing, reading.

I found an old SB Live! soundcard in a drawer of forgotten components and plugged it in.  Sound worked immediately, and so far Audacious has gone through about ten tracks without randomly muting, plus I checked my e-mail and the buzz did not occur.  Sadly, the Turtle Beach card has an unusual connector to the headphone jack up front, so I can't use that any more...but that's a minor complaint.

---

### Post by MobiusJedi on 2010-03-12
I love my santa cruz! Too bad Karmic doesn't seem to share my affection. snerd's work-around provides successful playback on my system, but only for one audio player thus far - audacious2.

---

### Post by Enigmapond on 2010-03-12
I wish I knew of this fix earlier..I also have this sound card in an older Dell Dimension 4400. My solution was to revert to a clean install of Jaunty...it works great now....:D

---

