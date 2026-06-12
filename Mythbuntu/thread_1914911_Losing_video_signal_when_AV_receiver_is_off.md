---
title: "Losing video signal when AV receiver is off?"
date: 2012-01-25
forum: Mythbuntu
---

### Post by ceenvee703 on 2012-01-25
Not sure if that's a great title, but that seems to be what's happening.

Using Mythbuntu for the past couple of years, currently on 11.04. Hardware setup hasn't changed recently: running HDMI from an Nvidia card (sorry, don't know from memory which one, maybe an 8400?) into an Onkyo AV receiver, and from there to my HDTV, at 1920x1080p. 

Software setup hadn't changed either, since in the past even doing updates has caused one thing or another to break (LIRC, Firewire channel changing, HD-PVR). 

Within the last two weeks, though, when I turn on my AV system and switch to my Mythbuntu box, I'll have a blank screen and my TV reports "no signal." I can get to a terminal with control-alt-F1 and then the TV recognizes a signal and shows me the terminal.

If I then do a restart and keep my system on, it boots fine, I get a video signal and MythTV front end, and everything's great. If I turn my system off and go away for a while, though, when I come back to it, blank screen again.

MythTV backend is continuing to work fine for recording programs.

Things I've tried:
* applying all the outstanding updates. Didn't help. (Luckily it didn't break anything either.)
* turning the system off at the Mythbuntu desktop instead of with MythTV frontend running. Same problem.
* Checking X log. I didn't see anything obvious but wasn't sure what to look for
* Searching forums and Google for "ubuntu blank screen": most deal with blank screen on boot, not blank screen after having a perfectly good screen.

Things I haven't tried yet:
* leaving the entire system on, and seeing if it is dying on its own after some amount of time, or if it's actually losing the signal when I power the system down.
* bypassing the AV receiver and running straight into the TV set (just as a test, I'd need it to go through the receiver for sound via HDMI)
* reinstalling Nvidia drivers

Any ideas appreciated. Thanks.

---

### Post by andree_b on 2012-01-25
Hm i would guess it is more likely a hardware problem like an electrical ground loop or may be even a dying PSU.

---

### Post by ceenvee703 on 2012-01-27
Just wanted to close this out in case anyone finds it--the MythTV box's video signal was doing just fine (I confirmed it by leaving TV on with no drop in signal, as well as VNCing into it). 

It was the inputs to my AV receiver, or the HDMI signal coming out of my receiver, that was to blame. If I turn on the system with the MythTV input selected (and get no signal), then switch inputs to my cable box (then get a signal), and then switch back to MythTV, I get a signal and everything's fine.

(And what might have done this was plugging a cheap switch into the back of the receiver... I had 4 HDMI devices but only 3 HDMI inputs. Needless to say the switch is gone now.)

Sorry for the false alarm. Thanks.

---

### Post by diesel48 on 2013-01-28
Same thing happens with my receiver sometimes. Not sure, it is an Onkyo. Did what you did and it works!

---

