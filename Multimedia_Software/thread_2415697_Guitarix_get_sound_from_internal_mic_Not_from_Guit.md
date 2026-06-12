---
title: "Guitarix get sound from internal mic Not from Guitar"
date: 2019-03-30
forum: Multimedia Software
---

### Post by beats2 on 2019-03-30
Hello.

I have troubled with Guitarix on Ubuntu studio 18.10.
Guitar sound is inputted correctly and sounded from monitor speakers like below.
[IMG]https://pbs.twimg.com/media/D25IcoEUkAAxwPd.png[/IMG]


But no input to guitarix though I connected with Jack like below.
[IMG]https://pbs.twimg.com/media/D244lrnU8AAIps9.png[/IMG]


My system is connected like below.

                    ----------------Audio Interface-------------Thinkpad x230-----------------------------
|My guitar  ->  steinberg UR22 mkII ->   Ubuntu Studio 18.10  -> speakers|
------------------------------------------------------------------------------------------------------

How can I redirect the guitar input to Guitarix.

Best regards,
Akihiro

---

### Post by beats2 on 2019-03-30
Thank you for your reading.

Now I can resolve the problem with following link.
[https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Set_the_default_sound_card](https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Set_the_default_sound_card)

Editing /etc/modprobe.d/alsa-base.conf and give snd_usb_audio higher priority.
```
options snd slots=snd_usb_audio,snd_hda_intel
options snd_usb_audio index=0
options snd_hda_intel index=1

```

Thank you.

---

