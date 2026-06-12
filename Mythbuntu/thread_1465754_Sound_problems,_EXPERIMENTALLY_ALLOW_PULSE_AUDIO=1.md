---
title: "Sound problems, EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1 doesn't work"
date: 2010-04-29
forum: Mythbuntu
---

### Post by lindsayward on 2010-04-29
Hi there...
I have a pretty simple wish (I hope). I have a DFI Lanparty mobo with dual  audio card and I want to output all sound out the HDMI output to my TV  except for rhythmbox, which I want to go out the analogue audio (to my  ceiling speakers).
When I run mythfrontend, it suspends pulseaudio and other sound (e.g. rhythmbox) stops. I tried uninstalling pulseaudio but that sort of messes up gnome and I couldn't get what I wanted anyway.
I have found lots of threads online where people have fixed this using the environment variable setting:
[FONT=monospace]
[/FONT]EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1

This does not work for me - MythTV still suspends pulseaudio. I don't think I've read any threads where it hasn't worked. 
I checked by typing env and the setting is there.

Any ideas how I can make this work?
I'm running Ubuntu 10.04 (not mythbuntu) with the myth that comes with it, 0.23-fixes.

Thank you in advance!

---

### Post by superm1 on 2010-04-30
> **lindsayward said:**
> Hi there...
I have a pretty simple wish (I hope). I have a DFI Lanparty mobo with dual  audio card and I want to output all sound out the HDMI output to my TV  except for rhythmbox, which I want to go out the analogue audio (to my  ceiling speakers).
When I run mythfrontend, it suspends pulseaudio and other sound (e.g. rhythmbox) stops. I tried uninstalling pulseaudio but that sort of messes up gnome and I couldn't get what I wanted anyway.
I have found lots of threads online where people have fixed this using the environment variable setting:
[FONT=monospace]
[/FONT]EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1

This does not work for me - MythTV still suspends pulseaudio. I don't think I've read any threads where it hasn't worked. 
I checked by typing env and the setting is there.

Any ideas how I can make this work?
I'm running Ubuntu 10.04 (not mythbuntu) with the myth that comes with it, 0.23-fixes.

Thank you in advance!

What output do you have selected in the general settings?  You need to select ALSA:pulse normally for it to not suspend.

---

### Post by lindsayward on 2010-05-01
Thanks for the reply.
I don't have the option ALSA:pulse when I look through the list, but I could set it manually to that by typing in the box.
The first time I did it, it seemed to work in that it didn't suspend the audio playing, but it also didn't play any sound in MythTV. I've tried a few other things and now when I set it to ALSA:pulse, I still get no sound in MythTV and it does suspend other pulse sound.
I've also posted another thread with my sound issues at:
[http://ubuntuforums.org/showthread.php?t=1467917](http://ubuntuforums.org/showthread.php?t=1467917)

---

### Post by fatbastard spice on 2010-05-01
You could try DEBUG_PULSE_AUDIO_ALSA_EMULATION=1. Seems this is what the environment variable is for 0.23.

I've also found the Pulse default option doesn't suspend the playback of the other applications and generally works well, but there's a bit of a delay on the playback that i haven't looked at trying to fix yet.

---

### Post by lindsayward on 2010-05-01
Thanks for the fast reply spice...

I have applied that new variable, and now I can use ALSA:hdmi in MythTV and still play rhythmbox and make other sounds too. Excellent, now I just need to get rhythmbox to go out a different sound device.

I sometimes wonder how we're supposed to find out these things. When I search google for DEBUG_PULSE_AUDIO_ALSA_EMULATION, this thread is the top response :)

---

### Post by lindsayward on 2010-05-02
:( I spoke too soon. Although I have sound coming out concurrently, I've lost all pulseaudio, it seems.
The volume preferences don't show up and when I run pulseaudio volume control, it doesn't work either. Typing pulseaudio in a command line, I now get:
Failed to load  module "module-alsa-source" (argument: "device=hw:0,4"): initialization failed.

I think this is the same as when I removed pulseaudio altogether before.
I'll try and backpedal, or perhaps I'll leave it and hope this whole thing gets fixed soon ??

---

