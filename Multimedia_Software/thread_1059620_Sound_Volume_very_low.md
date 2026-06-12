---
title: "Sound Volume very low"
date: 2009-02-03
forum: Multimedia Software
---

### Post by ryushe on 2009-02-03
Hi there, 

I have a dual boot machine here with 8.10 and XP.
Under XP my sound volume is pretty good, under Ubuntu it's very, very low compared to the output I get under XP. Thanks for VLC, which allows me to boost the output, but other apps that use sound simply don't output much at all, ie. not more than volume control allows when set to max.
My audio output is handled by pulseaudio at current, but I get the same if I use alsa or others for that matter.
Suggestions welcome on how to troubleshoot this, or anything basically telling me this is expected behavior.

---

### Post by rooster_fruit on 2009-02-04
I have the same problem, a fresh install of ubuntu 8.10, dual booting with windows (wubi)

on my system (i dont know about yours ryushe,) the volume output is off unless the volume level is above 75%

michael@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

michael@ubuntu:~$ lspci -v
...
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Gateway 2000 Device 0685
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
...

I had a previous install on a partition (which i removed and reinstalled through wubi) that had perfect sound output, nothing changed (that I know of) between the two installations

---

### Post by gackt on 2009-02-04
have you try to increase the master volume and PCM too?

---

### Post by rooster_fruit on 2009-02-04
> **gackt said:**
> have you try to increase the master volume and PCM too?

I'm not sure what PCM is, but I right clicked the volume control and upped the 'headphone' output, and the volume was back.

lets see it that fixes ryushe's problem too

---

### Post by morfeasrev on 2009-02-04
I have a soundblaster audigy LS and when I used windows I had the volume set to 50% and I could hear music on my way to supermarket (yes, while away from home).
Now on Ubuntu my sound volume is (almost) all the time to 50% so that I can see a movie:popcorn: on my couch or hear music.
No more music on my way to supermarket...:(

Help anybody???

---

### Post by gackt on 2009-02-04
> **rooster_fruit said:**
> I'm not sure what PCM is, but I right clicked the volume control and upped the 'headphone' output, and the volume was back.

lets see it that fixes ryushe's problem too

right click the volume icon > open volume control > choose alsa mixer 
you should see the pcm.

---

### Post by nufros on 2009-02-04
I'm noticing the same thing... I dual boot windows and ubuntu 8.04... I've noticed that in windows the volume is alot higher... AND I've noticed that my headphone output on the front of my computer is substantially louder than my speakers output on the back... I have checked alsa and pulse audio... it doesn't seem to matter because they're maxed out... it's definitely not a deal breaker for me because I don't like having my music too loud anyways, but it'd still be nice to know why my speakers on Ubuntu at 80% are weaker than my speakers on Windows at 25%...

---

### Post by rooster_fruit on 2009-02-05
> **gackt said:**
> right click the volume icon > open volume control > choose alsa mixer 
you should see the pcm.

i believe my pcm is max (now the sound turns off at less than 50%)

another thing i might note, sound in firefox is not working (youtube, etc)

EDIT: fixed the flash with:
[https://help.ubuntu.com/community/OpenSound#Flash](https://help.ubuntu.com/community/OpenSound#Flash)

---

### Post by dodderer on 2009-02-05
Kubuntu 8.04 in kmixer control only the headphone control works. master dead pcm too. to control volume from the panel on forum advice I right clicked and selected head fone in mixer I'm happy but dont know  mixer's controls dont work properly.

---

### Post by travmon69 on 2009-02-05
Try this command   ```
pulseaudio -k ; start-pulseaudio-x11
```

---

### Post by rooster_fruit on 2009-02-07
> **travmon69 said:**
> Try this command   ```
pulseaudio -k ; start-pulseaudio-x11
```

michael@ubuntu:~$ pulseaudio -k ; start-pulseaudio-x11
W: ltdl-bind-now.c: Failed to find original dlopen loader.
bash: start-pulseaudio-x11: command not found
michael@ubuntu:~$ 

i think i'm using OSS

---

### Post by travmon69 on 2009-02-07
maybe. i used the command in intrepid an jaunty   

try  ```
sudo /etc/init.d/alsa-utils restart
```

---

### Post by nufros on 2009-02-08
that doesn't make a difference for me... it's as though the front headphone jack and the rear audio jacks have been reversed somehow... I suppose I could plug the speakers into the front headphone jack, but I'd really rather not have to do that. I'm using Hardy... are any mods familiar with this problem?

---

