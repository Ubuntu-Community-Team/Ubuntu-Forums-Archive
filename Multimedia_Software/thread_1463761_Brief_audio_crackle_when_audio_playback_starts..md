---
title: "Brief audio crackle when audio playback starts."
date: 2010-04-27
forum: Multimedia Software
---

### Post by gencon on 2010-04-27
[SIZE=2][COLOR=Red]EDIT

I get the idiot of the day award. The fix described below works after a reboot.

Maybe someone can tell me what the implications of commenting out the final line of '/etc/modprobe.d/alsa-base.conf' are:

options snd-hda-intel power_save=10 power_save_controller=N

And/Or any way of getting rid of the audio crackle without getting rid of the power saving option? Or a compromise?

Thanks.

END EDIT[/COLOR][/SIZE]      

Original Post:

Using: Kubuntu/Karmic

Audio Output Device: HDA Intel (Realtek ALC883)

There's a small problem with my audio.

When any application plays some audio there is a crackle sound, which lasts less than a second, right at the beginning before the audio actually plays. If, for example, I'm playing a playlist of audio files, the crackle only happens right before the first audio file starts playing and it does not happen between tracks. The crackle also occurs at the beginning of a video (obviously when there is audio), and before the Kubuntu login and logout audio is played. It is as if the crackle occurs at the point of initializing the audio device for playback.

This page linked below, which I found while searching for a solution, says:
[http://www.ubuntugeek.com/ubuntu-tip-how-to-fix-crackling-noise-on-hda-audio-cards-in-ubuntu-9-10.html](http://www.ubuntugeek.com/ubuntu-tip-how-to-fix-crackling-noise-on-hda-audio-cards-in-ubuntu-9-10.html)

------------------------------------------------------------
"If you are getting crackling noise on HDA audio cards in Ubuntu 9.10. If yes, it is very easy to fix this issue all you have to do is remove the new power-save option in the new audio drivers.

Edit this file: /etc/modprobe.d/alsa-base.conf

Now you have to delete last two lines where you see power-save option."
------------------------------------------------------------

The last few lines of '/etc/modprobe.d/alsa-base.conf' are:

# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

Clearly the advise of the web page should have been to comment out the final line, which begins 'options snd-hda-intel power_save=...'.

I have tried commenting out the final line and at first I thought it reduced the volume of the crackle but with several tests I came to the conclusion that it sometimes reduces the volume of the crackle, but I am not entirely sure that this alteration is not to do with volume levels (even though I tried to make sure they were constant). Either way this 'fix' does not remove the crackle.

It is not a major issue but it is annoying and I'd like to get rid of the crackle completely.

Any advise would be greatly appreciated.

Many thanks.

---

