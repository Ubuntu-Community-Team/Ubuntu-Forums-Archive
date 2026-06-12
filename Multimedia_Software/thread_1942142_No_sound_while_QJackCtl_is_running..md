---
title: "No sound while QJackCtl is running."
date: 2012-03-17
forum: Multimedia Software
---

### Post by Splooshie123 on 2012-03-17
Whenever I start QJackCtl I am unable to play sounds. This only happens when it is running and quitting the application restores sound. It doesn't seem to matter whether the jack server is running or not.  For example, I start QJackCtl and then try to play an mp3 and get no sound. The mp3 won't even start playing.

EDIT: OK, I found out that QJackCtl suspends pulseaudio. This [UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation#Pulse_Audio") page says that installing pulseaudio-module-jack should make everything work out of the box. It didn't.
From the page:
"You should see virtual "Jack Sink" outputs and inputs in Audio preferences, and "[PulseAudio]("https://help.ubuntu.com/community/PulseAudio")" Sink (outputs) and Source (inputs) in jack (use Qjackctl or Patchage). "

The thing is, I checked the Audio preferences and didn't find anything except the defaults. No Jack Sink outputs or inputs. My guess is that the module isn't getting loaded.

---

### Post by Splooshie123 on 2012-03-23
Never mind. I figured it out and made a tutorial for it.

[http://ubuntuforums.org/showthread.php?t=1943224](http://ubuntuforums.org/showthread.php?t=1943224)

---

