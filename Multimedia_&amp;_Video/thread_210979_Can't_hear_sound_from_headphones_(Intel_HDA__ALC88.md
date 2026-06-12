---
title: "Can't hear sound from headphones (Intel HDA / ALC880)"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by THROBiX on 2006-07-07
Hi!

I'm using Ubuntu Dapper Drake (2.6.15-25 kernel) on my Quanta MW1 laptop.
My soundcard is Intel High Definition Audio, with Realtek ALC880-chipset.

My problem is that I only get sound through the internal speakers, not from the headphones. Even if I plug-in headphones in the jack, I still hear sound from the internal speakers.

I'm using Alsa 1.0.12rc1, compiled from source.

Here's the "lsmod | grep snd"-output:
```

snd_hda_intel          19476  1
snd_hda_codec         146736  1 snd_hda_intel
snd_pcm                81672  2 snd_hda_intel,snd_hda_codec
snd_timer              25220  1 snd_pcm
snd                    56292  6 snd_hda_intel,snd_hda_codec,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10760  2 snd_hda_intel,snd_pcm

```


And here's the "cat /proc/asound/cards"-output:
```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xc0000000 irq 169

```


And here's the "lspci"-output:
```

0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

```


Contents of "/etc/modprobe.d/alsa-base":
```

# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias char-major-116 snd

options snd major=116 cards_limit=1

options snd-hda-intel model=laptop-eapd

```


Here's the content of "/etc/modutils/alsa-base":
```

alias char-major-116 snd

options snd major=116 cards_limit=1

alias snd-card-0 snd-hda-intel

options snd-hda-intel model=laptop-eapd

```


I've tried using auto, z71v, laptop, and 3stack as "model", with no luck. I've even unmuted all the volumebars in alsamixer.
I've searched this forum too, and found others with same problem, just with another laptop (I think).. I have tried the solutions from the others, with no luck neither.

I would be very happy if someone have a solution, because I'm using headphones all the day (doesn't like to use external speakers).

---

### Post by BlakeEM on 2006-07-08
I have the same issue with my ASUS laptop, I have the exact same sound card

> 0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

I also use headphones a lot and had no luck as well trying to get it to work.

---

### Post by BlakeEM on 2006-07-08
I found a fix after some searching around.

[http://www.ubuntuforums.org/showthread.php?t=201657]("http://www.ubuntuforums.org/showthread.php?t=201657")

Worked for my laptop and seeing as you have the same sound card it may work for you as well.

Although you did say you tried z71v so maybe not =/

---

### Post by THROBiX on 2006-07-08
Thank you for trying to help me!

Unfortunately, it didn't work. I've tried model=z71v and the position-thingy before, and tried it now. The headphone-volumebar shows up. 
I hear no sound from the headphones, even if I slide the headphone-volumebar to the max (it's not muted). :(  And it still come sound from the internal speakers if I plug-in the headphones.

Maybe I can't manage to get it to work at all. :-k

---

### Post by THROBiX on 2006-08-06
For Quanta MW1-users:

I finally managed to get sound through the headphones!

Here's what I did:
* Make sure you have the 2.6.15-26-kernel (I think this is important, not sure)
* Downloaded the latest ALSA-packages from [www.alsa-project.org](www.alsa-project.org) (driver, lib, oss and utils)
* Unpacked the files
* Compiled them
* Inserted following to the end at the /etc/modprobe.d/alsa-base file:
  options snd-hda-intel model=lg position_fix=1
* Rebooted the laptop

Then I plugged in the headphones and got sound!
But, when the headphones was plugged in, there was still sound coming through the internal speakers, but I muted the "Surround"-mixer, and then the internal speakers are muted (I do always use headphones).

Now I'm really happy!

---

