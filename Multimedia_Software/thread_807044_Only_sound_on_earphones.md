---
title: "Only sound on earphones"
date: 2008-05-25
forum: Multimedia Software
---

### Post by bibawa on 2008-05-25
Hello,

I've just installed ubuntu 8.04, but when I start alsamixer I got the famous error:

```

steve@lnx-steve:~$ alsamixer
ALSA lib simple_none.c:1491:(simple_add1) helem (MIXER,'Headphone Playback Switch',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument


```

I've recompiled the alsa drivers and now I've sound via my earphones but not on my normal speakers, the sound om my earphones is very silent.

I've read a lot of post, tried a lot but nothings seems to works.

Ow, the output of the aplay -l:

```

steve@lnx-steve:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 4: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

I've set the Intel card to the default card with the command:

```

steve@lnx-steve:~$ asoundconf set-default-card Intel

```

Does anyone knows how to fix this big problem ? If someone must know more information, let me know !


Kind regards,

Steve

---

### Post by bibawa on 2008-05-25
someone ??

---

### Post by Gunman1982 on 2008-05-25
You probably already did this but slim chance you overlooked it ;)
Check the settings in your volume control in gnome if something is muted or set to low output.

---

### Post by bibawa on 2008-05-26
I've opened the gnome Volume control and set everything to 100%
When I play a test sound, I hear nothing, but when I plug in my earphones I hear the test sound.

I think its not normal that i've got the error:

```

steve@lnx-steve:~$ alsamixer
ALSA lib simple_none.c:1491:(simple_add1) helem (MIXER,'Headphone Playback Switch',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument

```

When I start Alsamixer.

Someone any idea why this error occurs?

kind regards,

---

### Post by bibawa on 2008-05-27
I've tried everything , but nothing seems to work :/

When I do aplay -l the output is the following:

```

root@lnx-steve:/home/steve# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 4: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

When I know open the gnome volume manager I see that there the device is Realtek ACL268, when I change the volume of the PHONE OUT the sound on my earphones changes.. 

So I think my modem and my audio device are on the same card and the alsa gives its output to the wrong card.

Can someone give me a possible solution to this problem?

:guitar:

---

### Post by depele on 2008-05-27
I've also the same problem....

---

