---
title: "Medibuntu, Maverick and libavcodec-extra-52 versions"
date: 2010-10-22
forum: Multimedia Software
---

### Post by andrew.46 on 2010-10-22
Hi,

I have added the Medibuntu repository and libavcodec-extra-52 so I can get aac encoding with libfaac and the repository FFmpeg under Maverick. When *-acodec libfaac* failed with a 'codec not found' message I had a closer look in Synaptic and saw 2 libavcodec-extra-52 packages:

[LIST]
[*]4:0.6-2ubuntu3 (maverick)
[*]4:0.6-2ubuntu+medibuntu1(packages.medibuntu.org)
[/LIST]

with the Ubuntu package, that comes *without* libfaac, being used by default. I enabled the Medibuntu version by 'Forcing' the version but I was interested to know if this is a known problem or simply something strange in my own setup?

Andrew

---

### Post by mc4man on 2010-10-22
> * 4:0.6-2ubuntu3 (maverick)
    * 4:0.6-2ubuntu+medibuntu1(packages.medibuntu.org)

Possibly a typo on your part 4:0.6-2ubuntu[COLOR="Blue"]2[/COLOR]+medibuntu1, but no matter - the medibuntu packages are versioned below the current mav. version.

Somewhat surprising because the change in mav. was on Oct. 5, going from 4:0.6-2ubuntu2 to ...ubuntu3

(what is odd this time is how the ver. #'s for the 'extra' packages don't match the reg. ffmpeg #'s - maybe they never did, I use my own.
Anyway medibuntu needs to re-build to ubuntu3+
> ffmpeg-extra (4:0.6-2ubuntu3) maverick; urgency=low

  * merge changes from 'ffmpeg' package

 -- Reinhard Tartler <siretart@tauware.de>  Tue, 05 Oct 2010 21:40:28 +0200

ffmpeg (4:0.6-2ubuntu6) maverick; urgency=low

  * fix dependency on libswscale-extra-0, LP: #637895

 -- Reinhard Tartler <siretart@tauware.de>  Tue, 05 Oct 2010 21:25:53 +0200

ffmpeg (4:0.6-2ubuntu5) maverick; urgency=low

  * Add flic video patch. Fixes CVE-2010-3429

 -- Reinhard Tartler <siretart@tauware.de>  Tue, 05 Oct 2010 21:11:41 +0200

---

### Post by andrew.46 on 2010-10-22
Thanks for confirming this mc4man, it is a little sad to see the aac encoding saga continue in this way for Ubuntu...

Andrew

---

### Post by mc4man on 2010-10-22
> it is a little sad to see the aac encoding saga continue in this way for Ubuntu...
I'm sure it was just a bit of an oversite - did [file a bug]("https://bugs.launchpad.net/medibuntu/+bug/665366") though probably not needed - you'd think someone at medibuntu would notice..?

Thought you may find this of possible interest (post 6
[http://ubuntuforums.org/showthread.php?t=1489353](http://ubuntuforums.org/showthread.php?t=1489353)

---

### Post by andrew.46 on 2010-10-22
Hi mc4man,

> **mc4man said:**
> I'm sure it was just a bit of an oversite - did [file a bug]("https://bugs.launchpad.net/medibuntu/+bug/665366") though probably not needed - you'd think someone at medibuntu would notice..?

I see you have not had the warmest of welcomes :). I no longer have a Launchpad membership in part because of carry on like that.

> Thought you may find this of possible interest (post 6
[http://ubuntuforums.org/showthread.php?t=1489353](http://ubuntuforums.org/showthread.php?t=1489353)

Indeed a very interesting development.

Andrew

---

### Post by mc4man on 2010-10-22
> I no longer have a Launchpad membership in part because of carry on like that.
I'm close there myself...
I know there is a certain protocol, ect., but sometimes the bs should be dropped and just fix or mitigate the issue.

a few ex. for sometime when you're bored (if ever..

At least here R.T. was reasonable after a bit of circling - [faad **decoding** disabled in xine]("https://bugs.launchpad.net/baltix/+bug/496010")
or a [small add. to vlc]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/620290") for maverick (though initial comment was off-putting

recently (going on for 3 months) this has been 'the straw that..'. the shame is every day people are posting w/ the same issue - [folders opening with anything but nautilus]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833")

After twice being [duped to a dead end]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/366963") and after making a few unwanted comments there, tried a new approach - bugged a [way to reduce the issue occurring]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194")- I'm sure it will be duly ignored.

On the slightly opposite end was the whole deal w/ [checkinstall]("https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/599163") - the maintainer was gung-ho to 'fix', after a bit do this, do that, ect., well, apparently it couldn't be be fixed so I guess no reason to return to the 'working' state seen in karmic and lucid... now out of the blue it's a "regression release"
(jeez - take 2 sec.'s, edit the source and be done with it, if someone ever figures out fstrans in debian/ubuntu great, if not, so what.

---------------------
Did happen to notice the other day - with the indeo5 sample, vlc should and does playback fine but there is the possibility that it won't, seems to be a minor bug there somewhere though can't figure out what yet (possibly something in the plugins cache

---

### Post by FakeOutdoorsman on 2010-10-23
I was about to confirm your bug as per tradition (and give a light flaming to the invalidator), but fortunately the package maintainer replied within the ten minutes it took me to get to my desktop with the Maverick VM.

---

### Post by mc4man on 2010-10-23
> I was about to confirm your bug as per tradition
Thanks for the thought - it looks like in a day or so people who wish to use the medibuntu libs should have an easier go of it.

(if you happen back here - did you ever resolve the 64 bit 'artifact' issue?

---

### Post by FakeOutdoorsman on 2010-10-23
> **mc4man said:**
> did you ever resolve the 64 bit 'artifact' issue?

No. [s]The related patch is still pending, but for now[/s] (duh, the patch I was thinking of was for another bug). I'm just capturing the DV tapes for this particular project and will begin encoding once yadif becomes usable.  I don't want to have to use yadif via MPlayer and a fifo to FFmpeg.  Another option is to wait for yadif and hqdn3d to make it into the x264 filter system.  I would guess that will be within a month but that's a pure guess.  Once that happens I will use x264 directly (with lavf support enabled).

In other news, the FFmpeg bug tracker has been moved to a new server so it is actually useful now instead of being agonizingly slow.

---

