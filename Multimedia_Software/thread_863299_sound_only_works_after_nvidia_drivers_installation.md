---
title: "sound only works after nvidia drivers installation, but then breaks again"
date: 2008-07-18
forum: Multimedia Software
---

### Post by Apertotes on 2008-07-18
hi, i am running ubuntu 8.04 (brand new install) on a Dell XPS M1330. when i installed it 4 weeks ago everything worked perfectly, but then, suddenly, last sunday, sound stopped working. i believe it was after an update, but i cant remember what package was updated.

anyway, i had sound on the login screen, and also after succesfully logging in, also, i was able to hear music from a game i was running through wine (EVE Online). But when playing music or video (tried many formats, mp3, ogg, avi, mkv, youtube, etc) nothing was heard. no error was given.

at the time i was running pulseaudio, so i switched to alsa. but the problem remained.

since i am quite a linux noob, after unsuccesfully trying many workarounds i found on the web, i reinstalled the system.

then everything worked fine again. i looked at sound preferences and it was all set as "automatic" except the last one, which was ALSA. i left it all as default.

yesterday, the system notified me of some updates (evolution, many lib***, libe***, and linux whatever kernel generic something 2.6.24.19). i upgraded the system, and then i lost the sound again. i had the exact same problem. i had sound on the login screen, and right after a succesful login, and also on EVE Online through wine, but i couldnt hear any video or music file at all. again, no error was shown.

of course, i tried rebooting many times, and also i booted up with different kernels on the grub menu (18, and 14) but that didnt solve anything.

then i tried going back to the pre-update state, so i looked up on the "history" list of sinaptic and forced the previous version of all the packages that had been updated, one by one, and each time rebooting and trying to play a video and a music file. no luck.

finally it was the turn of the "linux kernel whatever generic something 2.6.24.19". i unistalled them, and i rebooted. the kernel "19" had disappeared and i only had "18" and "14", so i chose "18", and to my surprise, screen&monitor configuration had been lost. but, what was worst, sound still didnt work.

i had to enable nvidia propietary drivers, and then i installed the updated drivers with EnvyNG. and this is the important part, read carefully, **when envy finished installing the nvidia drivers, i heard a tingling sound. so i tried playing video and music, and everything was working fine**. i was quite surprised.

anyway, i had to reboot the notebook cause of the nvidia installation, and when i got to the system again, sound was broken once more.

so, just to be sure, i launched envy and reinstalled nvidia drivers. when the installation finished, i heard the sound again, and once more sound was running perfectly. but with the next reboot, sound was lost again.

so i do not know what to do now. i am a complete noob, and i find myself completely unable to solve this problem.

---

### Post by wolfen69 on 2008-07-18
try [this]("http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio")

---

### Post by Apertotes on 2008-07-20
it worked!!! thanks a lot.

still, i would like to know, does anybody know why reinstalling nvidia drivers with envy made the sound work until the next reboot?

---

