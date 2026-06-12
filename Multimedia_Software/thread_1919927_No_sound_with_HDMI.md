---
title: "No sound with HDMI"
date: 2012-02-03
forum: Multimedia Software
---

### Post by davidtuti on 2012-02-03
Hi,
I have an ati HD 5770. I've installed Kubuntu 11.10 and I dont have sound with HDMI. Any help please?
```
aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC883 Digital [ALC883 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: Generic [HD-Audio Generic], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
david@MAQUINON:~$ david@MAQUINON:~$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]



```

---

### Post by wolfen69 on 2012-02-03
Install **pavucontrol** and see if there is a setting that helps. You did check the basic sound settings first, right?

---

### Post by davidtuti on 2012-02-03
> **wolfen69 said:**
> Install **pavucontrol** and see if there is a setting that helps. You did check the basic sound settings first, right?
Pavucontrol is everything ok.
I check all the settings.
When I'm trying to do a try. I use phonon and I get sound of my generic audio, but not with the HDMI. :(

---

### Post by caha-de-caha on 2012-02-10
i've got a similar problem with my gf430gt
in your pavucontrol (i think it should be the output tab) there is a list with something like
(HDMI)
(HDMI nr 4)
and so on, try to play with it. in my case it helped.

ps sorry for my english.

---

### Post by inobe on 2012-02-10
turn off IEC958 in pavucontrol, turn on hdmi output.

i'm using IEC958 at the moment.

[IMG]http://img853.imageshack.us/img853/5691/snapshot4e.jpg[/IMG]

a restart may be needed if you have trouble.

---

### Post by Yellow Pasque on 2012-02-10
If you're using the default/open-source radeon video driver, HDMI audio has not been enabled yet in current Linux distros: [http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY)

---

### Post by sonicb00m on 2012-02-11
> **Temüjin said:**
> If you're using the default/open-source radeon video driver, HDMI audio has not been enabled yet in current Linux distros: [http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNDY)

I hope they can get multichannel PCM working with the HD5450 card. From what I can find only stereo is supported. It also appears that all  audio streams are down sampled to 48 or 44 through the HDMI.

---

### Post by inobe on 2012-02-11
i want is this pavucontrol functionality in the mixer UI.

---

