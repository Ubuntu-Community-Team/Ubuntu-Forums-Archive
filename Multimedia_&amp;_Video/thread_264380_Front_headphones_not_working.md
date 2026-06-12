---
title: "Front headphones not working"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by gardfield on 2006-09-24
I have a desktop PC (Compaq Presario, P-IV, 3,4Ghz) where I just installed Ubuntu 6.06 (dual boot with Windows XP).
When I connect the headphone to the rear jack it works perfect, both the microphone and the headphone, but **no sound at all when I connect it to the front jack**. Both work fine in Windows. :confused: 

I have searched the forums and Googled around for the answer and found nothing so far. 

Can anybody help me with this?
Any suggestion would be really appreciated.

Here are the facts:
- I have already run the alsamixer and turned everything on. However, the <headphone> item doesn't have a volume bar, it only allows to be switched on/off, no volume adjustment. Is this normal?
- In the System - Preference - Sound, the Default sound card is *HDA Intel*
- The PC has a Realtek HD Audio Card (ALC-880):
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$ more /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
```

```
$ lsmod | grep snd
snd_hda_intel          18964  1
snd_hda_codec         142640  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm

```

If any additional info is required just let me know.

Thanks.

---

### Post by Henry Rayker on 2006-09-24
this is an incredibly weird problem. You're certain that the rear headphone jack works in Ubuntu? My reason for asking is because, typically, your front jack is just split off of the same line that goes to the rear. There shouldn't be a difference in which signals get sent where.

If the rear DOES work in Ubuntu, while the front doesn't, but they both work in Windows, then it may be a driver issue.

Maybe someone else can help out with this.

---

### Post by vendredi5h on 2006-09-24
I just move from Mandriva 2006 and installed Ubuntu 6.06 on my Dell Dimension 9150. I've got a really similar problem than yours but it's my front sound output that is working and the rear one is not. My sound card is "on board". I'm dual boot with Mandriva and it's working great there. 

Maybe we could compare something? Or maybe I could look at something on Mandriva? I'm afraid that I'm not very knowledgable regarding sound problem resolution so I don't know at what to look.

Yannick

---

### Post by gardfield on 2006-09-25
Henry,

I'm positive, the rear jack works fine in Ubuntu. I'm able to hear all media files in he examples directory (Mandela interview, etc.). When I change the headphone to the front jack then there's no sound. I agree it's a weird problem and that's why I'm asking around ](*,) 

Vendredi5h, I'm willing to compare our PCs but I'm not very skillful with hardware either so I wouldn't know exactly what to compare.

Suggestions anyone ?

thanks.

---

### Post by Kateikyoushi on 2006-09-25
Check [this]("http://www.ubuntuforums.org/showthread.php?t=168793&highlight=alc880+spdif") thread the last post is the most relevant.

Seems that notebook has the same sound card.

---

### Post by bluenova on 2006-09-25
miss posted.

---

### Post by IanW on 2006-09-25
The rear jacks for onboard sound cards are part of the motherboard, the front ones connect via a cable.
You may want to open your PC and ensure that the front jacks are actually connected to the motherboard.

---

### Post by gardfield on 2006-09-25
IanW, the front jack works fine in Windows so it is connected.

I tried the suggestion from the thread suggested by Kateikyoushi ...nothing :( 

Anything else?

Should I try to download and install any newer Alsa or Realtek driver?
I read somewhere that Realtek driver was really buggy,

---

