---
title: "stardict no sound after playing mp3"
date: 2008-05-19
forum: Multimedia Software
---

### Post by shelper on 2008-05-19
i am using stardict and using TTS to pronounce the words
but after playing mp3, it wont speak any more?

any idea?
tried different combinations in sound preferences
does not work.:(

thanks alot!

---

### Post by hvthao on 2008-08-05
Use alsa sound infrastructure to enable multi-sound from many apps. For example, playing mp3 by xmms (configure the audio output module "alsa"). Then the same for stardict, in the sound option "command for playing wav files", use "mplayer -ao alsa". mplayer is a powerful application for multimedia. You can install it from Ubuntu repository.

---

### Post by screenn on 2009-07-18
stardict uses esound (esd) system for pronounce a words, it uses esd like Gnome desktop manager, so you can choose esd in gnome-control-center -> sound -> esd, but when you chosen esd, you won't hear alsa sounds anymore.

---

