---
title: "Pulseaudi 5.1 Sound problem -Intrepid 8.10"
date: 2008-11-01
forum: Multimedia Software
---

### Post by ales on 2008-11-01
Hi Ubuntu friends,


yesterday I upgraded my 8.04 to 8.10. With 8.10 I got again by default installed Pulseaudio. In 8.04 I unsinstalled itbecause it was not able to play 5.1 sound - to use all my speakers. So I went back to ALSA, which I think is workin without any problems. 
Now in 8.10 a changed system preferences to be only ALSA used like in 8.04, but still many applicaions won't respect this. Unistalling is not possible, because it will remove gnomedesktop. There are absilutely no settings for Paudio to set up the use of 5.1 system. I don't unsertand, why it was implemented to Ubuntu, or why there is no option during installation for user wheter he /she wants to use ALSA or Pulse?

I have SB Live 5.1 and till 8.04 I had no problems with it. In 8.04 the oprion was to unistall pulse and all worked fine. In 8.10 it is not possible because od gnome desktop.

Also after changing the system preferences to ALSA, only GNOME player is able to play 5.1. Totem has set the sound to 5.1 but it is plain stereo on two front speakers. Same VLC... Also my music videos in totme and in all other players won't use all speakers.

Has enyone similar problem? Or has someone solved this? I have not found any solution in forums till now.

It would be nice and maybe useful to make a poll how many users prefer to use pulse and how many ALSA.

Thanks for any answer or help.

Ales


I solved it by installing some repositories to alsa and setting sound this way. See picture.

---

### Post by last_moromete on 2008-11-01
> **ales said:**
> 
I solved it by installing some repositories to alsa and setting sound this way. See picture.

What repositories did you install?

---

### Post by ales on 2008-11-02
Hello,


I dont' remember, so I give screenshots, what I have checked in synaptic. I have also disabled and removed pulseaudio to be loaded during startup in System > Preferences > Sessions.

I hope this can helpo. But I am not sure. I am not very good in understanding how it works....so usually I try.

A.

---

