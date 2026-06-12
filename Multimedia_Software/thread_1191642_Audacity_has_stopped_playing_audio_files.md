---
title: "Audacity has stopped playing audio files"
date: 2009-06-19
forum: Multimedia Software
---

### Post by cpetercarter on 2009-06-19
I use Audacity regularly to edit my podcast files and convert them to MP3s. Until today, no real problems.

Today I find that Audacity will load WAV or MP3 files as normal, but will not play them back. I get the error message that "Error while opening sound device. Please check the output device settings and the project sample rate."

I have not altered the output device settings (from ALSA default), but in any case any of the available output device settings produces the same error message. The project sample rate is 44100, as normal. Audacity even refuses to play back WAV files that it played back last week.

I have tried the following without success:

re-installing Audacity
deleting the Audacity configuration files (to force audacity to create new ones)
exiting all other programmes which use sound devices
running Audacity from "aoss audacity" in the command line

All other sound programmes (eg Audacious) seem to work normally; and I can upload, play-back and edit the sound files (ie the ones which Audacity will not play) in WavePad, using Wine.

It may also be relevant that Audacity today "greys out" frequently for several seconds.

Any idea what the problem might be?

---

### Post by newIsle on 2009-06-19
not that i think its gonna help, you seem to know much more about audacity then I....
but i get that same error when i was changing audio devices(specifially when i changed to OSS: /devdsp) trying to record a track..
..maybe somehow audacity or something else changed your defualt playback device..??

---

### Post by cpetercarter on 2009-06-19
I don't think it is that. I have tried all the options under edit > preferences input devices, and the result is the same.

---

### Post by tgalati4 on 2009-06-19
Is skype, or youtube or any other application running in the background?

sudo killall firefox-bin

That could tie up your sound hardware.

---

### Post by snapback77 on 2009-06-19
Had that problem. Went to PulseAudio.  Read Markbuntu:   [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

This worked for Audacity and my new HRT Music Streamer DAC.  Very Good by the way.

---

