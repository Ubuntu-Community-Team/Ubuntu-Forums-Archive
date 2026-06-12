---
title: "Ubuntu OK, myth loses sync on ATI"
date: 2008-08-18
forum: Mythbuntu
---

### Post by pootle42 on 2008-08-18
OK I know I shouldn't have bought an ATI card, but I got an offer..:)  - seemed like a good idea at the time.

Its a M3A78-EMH mobo (built in ATI graphics)
I've installed 8.04.1 as a default build and then used envyng to install latest ATI drivers.
while ubunti desktop displays OK, when I run Myth it's like a TV where H-Sync has failed (except its a monitor - and its sync'ed OK)

Looks like myth is getting its screen updates confused somehow.
see the attached files...

If a change screen res the appearance changes, but never comes out right.

Any idea what I do to fix this?

The drivers installed by envyng have dramtically improved the performance for scrolling etc. and if I go to TV its clearly a big improvement in performance, but not actually useful (same problem).
Without these drivers I get TV at about 2 frames a second, and scrolling is like a bad day on a 386 computer

---

### Post by Imitation on 2008-08-19
I'm not sure exactly what the issue is.

I have heard some people say they fixed this downgrading to Catalyst 8.5 or 8.6.  I tried going from 8.7 to 8.6 which is FGLRX 8.501 (I think) and it did not help.. infact it made the system more unstable.

As a work around you can run the Myth frontend from a terminal as such:

mythfrontend --geometry 640x480

The trick is to change the resolution to be 1 px smaller than your actual screen resolution.

For example if you're resolution is:

1366x768 use:      mythfrontend --geometry 136**5**x768

1920x1200 use:     mythfrontend --geometry 191**9**x1200


This stops the Myth frontend from going into fullscreen mode which is where it garbles.

Then you can right click the top XFCE panel and choose properties.  Turn on Auto-Hide.  You might like to add a 'Show Desktop' item also.

And that's the best I've come up with.  You are left with a small line (a few px) at the top of the screen but at least it works.

If anyone has an actual solution I'd love to hear it :)

---

### Post by pootle42 on 2008-08-19
Nice 1 Imitation, that's fixed the scan problem, unfortunately it just shows up that the is some serious confusion going on over de-interlacing, as I'm getting the odd and even scan lines as a sort of split screen.

Suspect this is a driver issue - ir clearly doesn't know how to handle an interlaced stream (or isn't being told it's interlaced)

DVD playing falls in a heap as well, but I'll dig into that a bit more before i post

UPDATE:
screen doubling fixed by changing de-interlace algorythm
DVD fixed by installing css bits - see update below

---

### Post by pootle42 on 2008-08-19
By setting the video scan to progressive, it stops doubling, but also there is no de-interlacing so its a bit of a mess with movement.

I also go DVD workin by installing the decss parts.  DVD also doubles and responds to setting video scan to progressive.

this thread [here]("http://www.phoronix.com/forums/showthread.php?t=8358")
suggests changing the deinterlace algorythm,

this is in the playback settings and is a much richer control than before.

lots of good data [here]("http://www.mythtv.org/wiki/index.php/Playback_profiles")

I still reckon there's a bug causing the doubling but it is easy to avoid now..

---

### Post by JugeHuge on 2008-08-20
Change playback profile or change playback profile deinterlacer different that bob.. Bob deinterlacer causes double image on ATI card

---

### Post by pootle42 on 2008-08-21
Thanks JugeHuge, that's fixed it nicely.

Now I'm just left with the problem I can't run full screen on this mobo.

---

