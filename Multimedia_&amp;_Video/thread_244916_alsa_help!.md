---
title: "alsa help!"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by [seif] on 2006-08-27
I have installing last version alsa-driver (alsa 1.0.12rc1) from sources.

At start alsa:
> $ sudo /etc/init.d/alsasound start
Starting sound driver: snd-intel8x0 done
No mixer config in /etc/asound.state, you have to unmute your card!



Modules are loaded:
> $ lsmod | grep snd
snd_intel8x0           36636  0
snd_ac97_codec        103072  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm                97156  2 snd_intel8x0,snd_ac97_codec
snd_timer              28548  1 snd_pcm
snd                    68972  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
snd_page_alloc         11912  2 snd_intel8x0,snd_pcm
soundcore              10784  3 snd,i810_audio


but :
> $ cat /proc/asound/cards
--- no soundcards ---:confused: 

I tried to do install alsa from repo, but it has not helped. :icon_frown: 

Soundcard:
> 
$lspci
....
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
....


Also you can look this ([http://linuxforum.ru/index.php?showtopic=23858](http://linuxforum.ru/index.php?showtopic=23858)) thread in Russian. :smile: 

Sorry for my English.

---

### Post by [seif] on 2006-08-27
up

---

### Post by [seif] on 2006-08-29
help ](*,)

---

