---
title: "onboard sound - can't adjust volume"
date: 2005-11-08
forum: Multimedia &amp; Video
---

### Post by linuxgrrl on 2005-11-08
I'm re-posting this question, this time with helpful information included ;) 

My onboard sound is working but I am unable to adjust the volume other than to mute / unmute channels.

My mobo manual does not say what hardware I have, but here are my diagnostics:

lsmod | grep snd returns:

snd_intel8x0 29984 2
snd_ac97_codec 64608 1 snd_intel8x0
snd_pcm_oss 47652 0
snd_mixer_oss 16768 3 snd_pcm_oss
snd_pcm 84872 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 23300 1 snd_pcm
snd 50276 6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore 9824 3 snd
snd_page_alloc 9604 2 snd_intel8x0,snd_pcm

Gnome's volume control applet shows two device options: "C-Media Electronics CMi9761 (OSS Mixer)" and "SiS Si7012 (Alsa Mixer)." Whichever one I choose, the same symptoms: sound works, mute/unmute works, but sliders don't.  My results with alsamixer and ossmixer are exactly the same  - even if I log in as root.

I have disabled the gnome sound server, because this is a mythtv box and I have to use ALSA.

Can anyone point me in the right direction to be able to adjust volume in alsa?

Thanks much,
Mary

---

### Post by kake on 2005-11-08
I've encountered the same problem with my BMP player using the OSS output plugin. Or I did just a couple of hours ago and just decided to look into. Haven't found much yet, but I have volume control working on my ALSA output. Try changing your Multimeda Systems selector (preferences) output to ALSA, also try setting your players to use ALSA as output. As for alsa mixer, the command is simply alsamixer. I can't remember if it was preinstalled or i got it's source.

The reason i'm looking into OSS is because I have some minor artifact issues with the audio of ALSA, and even heavier artifacts using the OSSsink in say amarok, but they were completly gone in the OSS plugin used in BMP.

Try setting your volume with the volume bar upper right after changing to the output you use in your volume control preferances (left click it and pref).

Anyways, are you sure all your outputs are set to ALSA? Funny, in the process of writing this i might have found a fix for my own problem. I'll let you know if i think it'll help you.

---

### Post by Hallavej on 2005-11-11
[QUOTE=linuxgrrl]
Gnome's volume control applet shows two device options: "C-Media Electronics CMi9761 (OSS Mixer)" and "SiS Si7012 (Alsa Mixer)." Whichever one I choose, the same symptoms: sound works, mute/unmute works, but sliders don't.  My results with alsamixer and ossmixer are exactly the same  - even if I log in as root.

I have disabled the gnome sound server, because this is a mythtv box and I have to use ALSA.

Can anyone point me in the right direction to be able to adjust volume in alsa?

Thanks much,
Mary[/QUOTE]

My "lsmod | grep snd" returns almost the same and i had the same problem. I fixed it by using ALSA and adjusting the volume with PMC instead of master. Change it in Volumen control-> preferences.
Also, make sure that your programs is in fact using ALSA. For example I had to change "output_plugin=/usr/lib/xmms/Output/libOSS.so" to "output_plugin=/usr/lib/xmms/Output/libALSA.so"
in the file: $HOME/.xmms/config to get xmms to use ALSA

---

### Post by linuxgrrl on 2005-11-12
[QUOTE=Hallavej]My "lsmod | grep snd" returns almost the same and i had the same problem. I fixed it by using ALSA and adjusting the volume with PMC instead of master. Change it in Volumen control-> preferences.
Also, make sure that your programs is in fact using ALSA. For example I had to change "output_plugin=/usr/lib/xmms/Output/libOSS.so" to "output_plugin=/usr/lib/xmms/Output/libALSA.so"
in the file: $HOME/.xmms/config to get xmms to use ALSA[/QUOTE]

Hmm, I tried this but still no success!  Based on a thread in another forum, I also tried running alsamixergui and tweaking every single channel (of many), including pcm and pcm2, and cant adjust volume.    :???:    (For the record, pcm mute/unmute does work.) 

any other suggestions?

---

### Post by kake on 2005-11-14
If it was me I would most likely update the Alsa drivers to match atleast 1.0.9b. You can check your current version in /proc/asound/version . However I belive that the default ubuntu kernel with breezy 5.10 comes with Alsa 1.0.9. You could get a new kernel or just patch your current kernel with updated alsa. This information can be found on alsawiki for one.

Before going to such lengths you might want to be sure that alsamixer is controlling the right device. Default device is 0. Try running the command alsamixer -c 1

Some cards have reported issues like these, and the recommended course of action was (as always) to update to drivers.

---

### Post by art2003 on 2005-11-29
I have exactly the same on board sound card and exactly the same problem.
Volume is at full blown whatever I do, except muting it.
So I can have 0% or 100% nothing in between.
Output sink is set to alsa, have also tried esd, same thing.
If I set it to oss then it doesn't work if it helps anybody.

This system is an upgrade from hoary to breezy. In hoary the sound was fine.

It is listed in bugzilla and marked as fixed, it involves changing /etc/asound.conf to use a softvol type.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=7997](https://bugzilla.ubuntu.com/show_bug.cgi?id=7997)

---

