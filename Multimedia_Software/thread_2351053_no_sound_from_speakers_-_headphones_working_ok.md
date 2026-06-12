---
title: "no sound from speakers - headphones working ok"
date: 2017-01-30
forum: Multimedia Software
---

### Post by funked up on 2017-01-30
Hello guys, there is no sound coming out of my speakers but when I use headphones it works fine.
A few days ago all was working fine.

Now when I open audio settings, in the output tab there is only an option for headphones.
I searched in google but most cases are posted years ago. As suggested in some cases I typed 'alsamixer' in a terminal and checked everything there but nothing helped.
 I reinstalled alsa and pulse audio via terminal. Now I don't have the general settings options left on the screen and even the volume bar on top right of the screen has disappeared. I still can hear sound only through my headphones.

Anyone knows what's going on?

I'm using an old thinkpad R61i with ubuntu 14.04 LTS.

---

### Post by ajgreeny on 2017-01-30
Check the volume settings for both headphones and speakers in pulseaudio volume control **Output Devices** tab as it sounds as if you have headphones set at the correct level but speakers are muted.

Hardware devices are dealt with separately in pulse and users often find this strange and have the same problem as you are suffering.

---

### Post by funked up on 2017-01-30
As I mentioned before, when I reinstalled alsa and pulse audio via  terminal (as many suggested) I lost all control panel settings. But before that when I still could go into pulseaudio volume control Output Devices there was only the option for headphones. 

In 'alsamixer' via terminal I have set them both at 100% but only headphones work.

---

### Post by benlyboy on 2017-02-01
hey there, you didn't say if this is a new problem on a older system, or a new system that the sound has never worked on? If its an older system have you made any changes or done updates?

---

