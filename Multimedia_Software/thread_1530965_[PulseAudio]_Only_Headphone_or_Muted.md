---
title: "[PulseAudio] Only Headphone or Muted"
date: 2010-07-14
forum: Multimedia Software
---

### Post by zeroXcool on 2010-07-14
Hi everyone,
i've got a problem with pulseaudio and hope someone has a good idea ;)

Frist things first:
Alsa is Setup correct and working fine (tested with purged pulseaudio package, i got sound without pulse)

I think the Problem is the following:
If I look at alsamixer and pulse settings simultaneously i can see that in alsamixer that the headphone switch is active (so no sound on internal speakers) but if i disable headphone in alsamixer => the pulse audio settings switch the global mute switch on (so no sound). and if i disable the global mute in pulse settings the headphone switch in alsamixer is back on....
This leads to no sound at all over the internal speakers

System Info:
* Ubuntu 10.04 LTS (fresh install)
* Notebook: Acer Aspire 9813wkmi
* Soundcard Info (from Alsa "options snd_hda_intel model=acer-aspire" is needed and working):
```

zc@mobile:~$ cat /proc/asound/cards 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd2300000 irq 22
zc@mobile:~$ find /proc/asound/card* -type f | grep codec | xargs grep "^Codec\|^Vendor Id\|^Subsystem Id\|^Revision Id" | grep -B2 -A1 $(lspci -nv | grep -A1 0403 | grep Subsystem | sed 's/://g' | awk '{ print $2 }')
/proc/asound/card0/codec#1:Codec: Conexant ID 2bfa
/proc/asound/card0/codec#1:Vendor Id: 0x14f12bfa
/proc/asound/card0/codec#1:Subsystem Id: 0x1025006c
/proc/asound/card0/codec#1:Revision Id: 0x90000

```

---

### Post by lidex on 2010-07-17
You look like a prime candidate for the linuxant drivers. You'll find them here:
[http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/")

---

### Post by zeroXcool on 2010-07-19
Hey first reply, thx !

Alsa is working (when removing Pulse or just Plugin in a Headphone I got sound), but i'll give it a try and reply if it helped.

---

### Post by zeroXcool on 2010-07-22
Everyone with the same Problem:
You can try this, it does not fix Pulse it removes Pulse but keeps the Metapackage ubuntu-desktop and guides you on how to install the alsa-panels for gnome: [http://www.altfire.com/main/news/index.php?news_id=504](http://www.altfire.com/main/news/index.php?news_id=504)

---

