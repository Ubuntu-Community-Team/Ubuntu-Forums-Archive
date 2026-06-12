---
title: "ALI m5455 no sound"
date: 2006-12-11
forum: Multimedia &amp; Video
---

### Post by TchaTcha on 2006-12-11
Hello folks,

My sound in Ubuntu never worked, i found out that the udev didnt find the right module to load. Thereafter i put the module to load on /etc/modules.

I have a ALI M5455 PCI AC-LINK ONBOARD sound card, and needed the snd-intel8x0 module to start it.

Even thou after i put the module to load alsaconf now find it and use the rigth driver to initilize it, in the end of the alsaconf script, when he uses the amixer to load up volume the following error occur, and this is my alsaconf output:

> 
Unloading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-ac97-bus sn d-pcm-oss snd-mixer-oss snd-pcm snd-timer snd-page-alloc.
Building card database...
Running update-modules...
Setting default volumes...
amixer: Mixer attach default error: No such device


===============================================================================

 Now ALSA is ready to use.
 For adjustment of volumes, use your favorite mixer.

 Have a lot of fun!



I remember one time, only one, getting a lot of messages saying:

shell-init: error retrieving current directory: getcwd: cannot access parent directories: File or Folder not found

i dont even know if its it has something to do with the sound problem.

My alsamixer output is

> 
alsamixer: function snd_ctl_open failed for default: No such device


I realize the /dev folder do not have /dev/dsp and the only thing in the /snd folder is /snd/timer

Any ideias on whats happening?

Thanks
Tcha

---

### Post by kedde on 2007-02-17
hey
I got the same onboard soundcard
sound ( ADI AD1888 )
```

lspci | grep 'audio'
ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)

```

What I did to make it work was:
edit  /etc/modprobe.d/alsa-base file (sudo gedit /etc/modprobe.d/alsa-base)

and insert the following:
 
```

# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-intel8x0
options snd-intel8x0 index=0
options snd-intel8x0 buggy_semaphore=1
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

# OSS/Free portion - card #1
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

# OSS/Free portion - card #2 (cmipci)
alias sound-slot-1 snd-card-1
alias sound-service-1-0 snd-mixer-oss
alias sound-service-1-3 snd-pcm-oss
alias sound-service-1-12 snd-pcm-oss


```

Reboot

Hope it helps.

---

### Post by majafo1 on 2007-04-04
thank you kind sir!

---

### Post by Benzwali on 2007-05-21
Thank you for that post. Not a clue what Im doin with linux, installed ubuntu coz i was bored... after much googling ur solution came up and worked without a hitch, thanks so much

---

### Post by tanith on 2007-06-07
Hi, that didn't work for me (maybe because I have 2 sound cards).

But this works:
```
sudo gedit /etc/modprobe.d/alsa-base
```
We comment this line:
```
#options snd-intel8x0m index=-2
```
and after that line we add this:
```
options snd-intel8x0 buggy_semaphore=1
```

I have Fiesty Fawn 7.04

---

### Post by Woodman on 2008-06-09
Thanks alot kedde! Worked like a charm. :)

---

### Post by snowflake_falls on 2008-07-18
i don't understand how to use that code...could someone help me, couls someone explane me?

---

