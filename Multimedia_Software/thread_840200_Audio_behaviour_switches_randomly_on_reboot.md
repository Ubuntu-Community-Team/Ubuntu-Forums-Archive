---
title: "Audio behaviour switches randomly on reboot"
date: 2008-06-25
forum: Multimedia Software
---

### Post by bastler on 2008-06-25
Hi there.

I'm posting here because *surprise* I am troubled by my audio hardware.
I read the comprehensive audio guide and have been searching this forum and the net for days, found interesting clues, but so far nothing that really solved my problem. So here it is in the hopes that someone has seen this before and can point me in the right direction:


My Setup:
=========

- I use ubuntu 8.04 with the gnome desktop environment, but mainly kde-apps for multimedia (amarok, kaffeine, k3b, soundkonverter, kopete) because... well... they are just so much better!

- Hardware is a VIA 8235 AC97 audio controller onboard a ASUS A7V8X mainboard. I have stereo speakers connected to the analog-out and 2 seperate high-end 5.1-setups connected to the SPDIF.
The system is 32bit x86.

- I run ALSA to fire the sound system, as to my knowledge PulseAudio does not support ac3/DTS passthrough without lossy recoding.



Desired Behaviour:
==================

While only stereo sources are playing:
.     output audio from all running apps through both the analog,
.     as well as the SPDIF simultaneously.

While DolbyDigital / DTS multichannel audio is playing:
.     exclusively passthrough the multichannel data stream to the SPDIF out
.     ignore all other audio sources for the SPDIF
.     I don't care what the analog outputs do during ac3/DTS playback

I don't need volume control on any output since it's more convenient for me to control playback volume through the external amplifier anyway.



Observed behaviour:
===================

When I freshly install ubuntu the system behaves just like described above, so everything is fine.

After a random amount of reboots (anything from 1 to say... 500) suddenly the system behaviour changes to one of 3 possible scenarios described below. From then on I cannot reach the "desired behaviour" any more no matter what I try, but the system seems to switch randomly between the three scenarios described below on reboot.


Scenario 1: no error messages, no output
========================================

All applications run fine, I can start amarok and play an audio file. Playback starts normally, but I get no sound whatsoever.
Neither from media players, nor from the system itself.
Playing with alsamixer doesn't help (I systematically tried every possible combination and yes, there are many!).
Manually shutting down ALSA, deleting asound.state and rebooting however often (not always) leads to scenario 3.


Scenario 2: analog works, SPDIF stereo acts up, ac3/DTS works
=============================================================

Analog outputs work nicely and does everyting as expected, but stereo sound is not sent to SPDIF.
When I start playback on <media player of choice> the SPDIF remains silent. I can get it to work by going to the system--> audio settings and playing a test tone to the soundcard. Only then the SPDIF turns on, I don't hear the test tone, but I hear the music. The quality is very poor though, I suspect it's downsampled to 22KHz or less.
The test-tone-menu from the system preferences is locked up during that time (can't even force it closed with kill -9).
As soon as I interrupt playback (pause/stop/next/previous song) the SPDIF outputs the test tone and the settings window responds again.
After quitting the test tone the SPDIF goes silent again.

ac3/DTS passthrough works great though.
Playing with alsamixer only causes SPDIF to stop functioning at all.
Removing asound.state as mentioned above sometimes leads to scenario 3, sometimes kills sound alltogether.



Scenario 3: both analog and SPDIF work fine, but not simultaneously
===================================================================

Using the "IEC958 Playback AC97-SPSA" lever of alsamixer I can switch bewteen "working analog and silent SPDIF" and "silent analog and working SPDIF".
Whatever I try, I have not yet found a way to get them working simultaneously.

Ghosts in the Machine 1: 
when I use "aplay -D hw:0,x" (x=1,2) to send a file to a specific subdevice the numbering does not seem to be consistent.
sometimes hw:0,0 activates the SPDIF for output and hw:0,1 the analog plugs, sometimes it's the other way around, sometimes both activate the analog output and SPDIF doesn't respond at all.

Ghosts in the Machine 2:
when I select the SPDIF in this scenario to play stereo sources only one of my 2 SPDIF-receivers accepts the signal as valid. The other one (hooked up to the very same cable) discards the signal and doesn't play anything.
again, ac3/DTS works fine with both receivers, as does sound in MS Windows, so it's not a cabling issue.



Annotations
===========

Usually I do not have an .asoundrc file to fine tune ALSA.
I have been playing around with various configurations in .asoundrc with varying outcome, but none reliably improved my situation.
I don't know how to get ALSA to route audio to both outputs simultaneously using asoundrc, and usually when I try ALSA complains about my syntax and shuts down or simply ignores the file.


I know, "I did nothing and suddenly it changed" is a classical response that every admin loves to hear, but I really cannot think of anything I did to trigger the changes. The only thing I can imagine is that I frequently play multichannel DVDs while kopete etc are still running and outputting stereo sound, so at some point the sound card might be busy with ac3 when requested to also play a stereo sound by ALSA, but that shouldn't cause the whole sound system to break down in my opinion...


I suspect there's some kind of race condition somewhere while ALSA or it's modules are loading but I'm not so much of a linux genious to find it myself.

If anyone knows a solution to this mystery please explain! Any help is greatly appreciated

---

### Post by markbuntu on 2008-06-25
Are you getting regular updates?

Many people have reported problems with audio caused by the kernel updates. You might try booting to a previous kernel and see if that fixes your problem.

---

