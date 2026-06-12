---
title: "No Sound in MythTV (but sound in Ubuntu!)"
date: 2010-11-24
forum: Multimedia Software
---

### Post by Ansemx324 on 2010-11-24
Okay, so Ill try to make this as short and sweet as possible.

I have Ubuntu 10.10 64 bit and have sound. I can play a video with mplayer and get sound, and "test" in Preferences-->Sound-->Hardware sends the "bump" sound to the speakers just fine.

Unfortunately MythTv doesnt have any sound when trying to play videos (MythVideo). Not trying to do ANYTHING else in MythTV besides the videos right now, but as far as I know there is no sound for mythtv.

I have looked all over for answers to this, I try to figure things out before posting for help and have worked on this for days.

Things I have tried:

Installing proprietary driver for video card (Im using onboard 880G chipset). Didnt work

Created an alsa asound.conf file. I used a template that is here
[http://www.mythtv.org/wiki/Configuring_Digital_Sound](http://www.mythtv.org/wiki/Configuring_Digital_Sound)
and just added card 1 device 3 to digital and default. (in aplay -l, this is the one that says HDMI that I think I should be using, since HDMI is the only thing going to my TV). Didnt work.
       --Note! I also don't hear anything when saying "aplay -D digital /home/me/soundfile.au"
            Says its playing but I dont hear anything...

I found out that Ubuntu not uses pulseaudio per default, and thought this may interfere with alsa? I uninstalled puslaudio and....still didnt make a difference.

Now Ive reinstalled Ubuntu 10.10 64bit for a fresh start and remade that asound.conf file (definitely think I need that.

Any suggestions? Ive been working on this for days and just cant figure it out! Something is probably wrong with alsa since aplay wont play anything...

PS: Speaker-test with aplay does send the static to the speakers...so sound CAN go through, but mythtv and aplay just wont have it.

Thanks for the help!

---

### Post by bance on 2010-11-24
Have you checked your device in alsamixer....... make sure it is not muted, ubuntu uses pulse audio but myth uses alsa. I'm no expert but I hope this helps!

Good luck Steve.

---

