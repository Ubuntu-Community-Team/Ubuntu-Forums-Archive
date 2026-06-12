---
title: "Recurring sound failure"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by GlennB on 2006-10-28
Hi All,

I'm getting really frustrated with a recurring audio failure on my laptop. After a reboot, all audio works fine - real player, desktop sounds, streaming audio, ogg files etc are all just dandy.

At some point, for an unknown reason, the sound will fail on all sources and formats, and the only way I can restore it is with a hard reboot. I'm stumped.

The machine is a Dell Inspiron 1300. alsamixer sees the audio device as a SigmaTel STAC9200, lspci says it's a 82801 Intel device, and gnome mixer reckons I have the STAC9200 (OSS mixer) and "HDA Intel" (Alsa device).

when the sound fails, I've checked that the module is loaded (it is) and all applications act as though they are playing a file - no errors anywhere. 

I tried restarting alsa using

```
sudo /etc/init.d/alsa-utils restart
```

as recommended in a troubleshooting guide here, but still no audio. Is there some other way of restarting the sound server completely without resorting to a reboot?

I don't have any evidence yet, but I'm starting to suspect that the audio breaks after I've used realplayer (non-free).

Thanks,

Glenn.

---

### Post by HwyXingFrog on 2007-02-13
I am also having this exact problem with a Dell Latitude D820 laptop.

I am running 6.10, and I have Amarok installed.

And I will have no more sound at random times

---

