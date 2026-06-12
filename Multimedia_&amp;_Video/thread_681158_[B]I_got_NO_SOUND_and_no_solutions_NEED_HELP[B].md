---
title: "[B]I got NO SOUND and no solutions NEED HELP[/B]"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by tabris37 on 2008-01-28
My computer has no sound. so far Ive tried everything I can think of but nothing has worked. Part of the problem is that i dont know what Im doing. The output for **$ lspci -v | grep Audio** yields 00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03). So I know my integrated sound-card is recognized. it is also enabled in the BIOS, so it should be operational. I went to the Realtek website and found drivers for Linux but they are out of date and don't work. I have the Alsa mixer unmuted and the external amplifier is unchecked. I don't have any luck with the Sound Preferences and I have all the sound playback options set to Autodetect. I need help I dont know what options I have left and I sure dont have any solutions left. please dont leave me suffering in silence.

---

### Post by Metaljaz on 2008-01-28
Right click on the volume button in the top right hand corner. Open volume control and make sure that PCM is not muted. Mute PC speaker and Line in to start with.
Then again right click on the volume control button and select preferences. try selecting alsa mixer and then scroll down to PCM. Give that a try.

if all else fails try these troubleshooting threads/wiki:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

