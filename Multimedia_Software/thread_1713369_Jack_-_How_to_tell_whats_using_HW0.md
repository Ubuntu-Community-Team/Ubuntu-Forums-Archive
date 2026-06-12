---
title: "Jack - How to tell whats using HW:0 ?"
date: 2011-03-24
forum: Multimedia Software
---

### Post by CFet on 2011-03-24
Hi All,

Receiving this error from Jack:

Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.

> Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xf9ff8000 irq 47 the playback device "hw:0" is already in use...

How can tell what is using hw:0?

I have tried

```
pasuspender qjackctl
```

and

```
sudo /sbin/alsa force-reload
```

with no luck.

Any guidance/help would be appreciated.

---

### Post by cchhrriiss121212 on 2011-03-24
Another program, shut down everything that uses audio and try again.

---

### Post by CFet on 2011-03-24
> **cchhrriiss121212 said:**
> Another program, shut down everything that uses audio and try again.

Thanks for the reply, I already had everything closed. It seems to be in use right from boot. 

My specific question: is *how* I can tell *what* is using HW:0. Are there commands or a set of commands that can tell me?

---

### Post by cchhrriiss121212 on 2011-03-24
System monitor or top will show you everything that is running. But on a fresh boot, nothing will be using ALSA.
I have seen another thread like this where jack claims a device is in use on a freshly booted system, it could be a bug.

---

### Post by CFet on 2011-03-25
Thanks for the help. From what I can tell in the forums, it may be my soundcard: SupremeFX X-Fi. Seems to be nothing but problems with these software based cards.

So, to re-direct my discussion. Anyone have some solid suggestions for a good sound card in the $200 Max range with awesome compatibility? I currently have a Logitech 5.1 Surround system I'd love to be able to maximize.

---

### Post by cchhrriiss121212 on 2011-03-25
The ASUS Xonar range have good support, and the reviews I've seen indicate they are good quality. The ALSA database will show you what sound devices are supported and to what extent, here is the ASUS page:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus)

---

### Post by cavalier911 on 2011-03-25
Determine what process is locked on HW:0
```
fuser -v /dev/snd/pcmC0D0p
```

Kill the process which is locked on HW:0
```
fuser -k /dev/snd/pcmC0D0p
```

Those are zero's not capitol O's

---

### Post by CFet on 2011-03-25
> **cavalier911 said:**
> Determine what process is locked on HW:0
```
fuser -v /dev/snd/pcmC0D0p
```

Kill the process which is locked on HW:0
```
fuser -k /dev/snd/pcmC0D0p
```

Those are zero's not capitol O's

cavalier911 For the WIN! Finally, something that can definitively tell me. Pulseaudio is the culprit apparently. Still, I'm going to look into a new soundcard. Thanks very much folks, going to tag this as Solved when I figure out how to :P.

---

