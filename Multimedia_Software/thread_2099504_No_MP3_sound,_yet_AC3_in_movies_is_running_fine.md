---
title: "No MP3 sound, yet AC3 in movies is running fine"
date: 2012-12-29
forum: Multimedia Software
---

### Post by mc@2 on 2012-12-29
My setup is an Asus AT3IONT-I hooked up via HDMI to my AC3 capable TV. The unit is running Ubuntu 12.04 with XBMC

Movies are playing fine, yet when i play an mp3 through the XBMC interface is get "failed to initialize audio device".  I've enabled logging and found the first error:
[FONT="Courier New"]ERROR: Initialize - pcm_open_lconf, alsa error: -22 - Invalid argument[/FONT]

I couldn't find any reference for this error. Anyone knows what to do with this?

aplay -l
[FONT="Courier New"]**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/FONT]

xbmc.log:
[FONT="Courier New"]22:38:17 T:3006618368    INFO: PAPlayer: Playing /home/user/Music/song.mp3
22:38:17 T:3006618368   DEBUG: PAPlayer: Creating new audio renderer
22:38:17 T:3006618368    INFO: CAudioRendererFactory: no input channel map specified assume windows
22:38:17 T:3006618368    INFO: CPCMRemap: Configured speaker layout: 2.0
22:38:17 T:3006618368    INFO: CPCMRemap: I channel map: FL,FR
22:38:17 T:3006618368    INFO: CPCMRemap: O channel map: FL,FR
22:38:17 T:3006618368   DEBUG: CPCMRemap: Downmix normalization is disabled
22:38:17 T:3006618368   DEBUG: CPCMRemap: FL = FL(1.000000*)
22:38:17 T:3006618368   DEBUG: CPCMRemap: FR = FR(1.000000*)
22:38:17 T:3006618368   DEBUG: RemoveActiveDevice - Removing device 1
22:38:17 T:3006618368   DEBUG: SetActiveDevice - SetActiveDevice from 0 to 2
22:38:17 T:3006618368   DEBUG: RemoveActiveDevice - Removing device 0
22:38:17 T:3006618368   DEBUG: Initialize - using alsa device default:CARD=NVidia,DEV=2
**22:38:17 T:3006618368   ERROR: Initialize - pcm_open_lconf, alsa error: -22 - Invalid argument**
22:38:17 T:3006618368   DEBUG: SetActiveDevice - SetActiveDevice from 2 to 1
22:38:17 T:3006618368   DEBUG: RemoveActiveDevice - Removing device 2
22:38:17 T:3006618368   DEBUG: CGUIAudioManager::Initialize
**22:38:17 T:3006618368   ERROR: Creating a Null Audio Renderer, Check your audio settings as this should not happen**
22:38:17 T:3006618368   DEBUG: RemoveActiveDevice - Removing device 1
22:38:17 T:3006618368   DEBUG: CGUIAudioManager::DeInitialize
22:38:18 T:3006618368   DEBUG: SetActiveDevice - SetActiveDevice from 0 to 2
22:38:18 T:3006618368   DEBUG: RemoveActiveDevice - Removing device 0[/FONT]

---

### Post by SR_ELPIRATA on 2012-12-30
Erm... you know xbmc has a really good support forums do you?

Only with your model I got many threads about it, like:

[http://forum.xbmc.org/showthread.php?tid=140198&highlight=AT3IONT-I](http://forum.xbmc.org/showthread.php?tid=140198&highlight=AT3IONT-I)

In any case, nobody here will be able to help you much with xbmc logs (unless they happen to be devs also hanging in here :) ), this is mostly ubuntu support.

I love xbmc :) And I love this and their forums, and to each their own I guess.

When you check their forums, go to the Linux section, and then read the first post about submiting bug reports and such, done the way they ask is the best way to get things solved.

Out of curiosity, why do you have it connected directly to your tv?

I remember some time ago I had a problem with some video files, like MP4 and AVIs would work but not the MKV files, or with DTS vs AC3 and such, I remember unchecking where it says AC3 capable receiver and it solved many things.

ELP

---

