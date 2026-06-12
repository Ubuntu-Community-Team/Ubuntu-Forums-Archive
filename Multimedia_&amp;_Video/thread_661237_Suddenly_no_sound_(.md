---
title: "Suddenly no sound :("
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by stardustdk on 2008-01-07
Hey All.

I have enjoyed Ubuntu Gutsy for a while, but without any installations/removing packages there are no sound whatsover. :confused:


I tried the usual stuff: Testet the sound, reinstalled alsaxxxx, checked alsamixer. 

Nothing helped ???

Suggestions please.

Best regards

Stardustdk

---

### Post by henrikbrink on 2008-01-07
Hi

I have the exact same problem. Suddenly, after using Gutsy fine since it came out, there is no sound on my laptop whatsoever. Not in any program.

The hardware is found:

```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

Alsa knows about it:

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

But when I run fx aplay:

```

$ aplay
ALSA lib pcm_direct.c:867:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:876:(snd_pcm_dmix_open) unable to initialize slave
aplay: main:545: audio open error: Invalid argument
```

And there are similar results for any other sound producing application. Some program says something similar to the above, and some says the sound card is busy or locked. Are there some software lock for alsa or whatever that can prevent anything from using the sound card?

It should be noted that in Hardy test 2 it is working fine, but if I boot from Linux Mint 4 live cd, the same problems appear. Almost as if it is locked for everything but the newest OS. Something about the kernel or Pulse Audio? But why the sudden change?

I've been over every sound problem thread and bug report google could find, and none have helped.

Thank you for any input!

---

### Post by stardustdk on 2008-01-08
My audio hardware is:

 lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Is this a Ïntel or Ubuntu fault?

Best regards

Stardustdk

---

### Post by msmarino on 2008-01-30
Hi all

Me too! I suddenly lost all sound 2 days ago. 

It seems to be ALSA related as if I set System/Preferences/Sound to Open Sound System it works.  Mixer seems unaffected, just the sound output.

just for reference:

```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
```

```
$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC883 Digital [ALC883 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```

```
$ aplay Gnarls\ Barkley\ -\ Crazy.mp3 
Sonando datos en bruto 'Gnarls Barkley - Crazy.mp3' : Unsigned 8 bit, Ratio 8000 Hz, Mono

(Silence ?!)
```

---

### Post by iiinked on 2008-01-30
Another one chiming in to say I have absolutely sound. 
I have a laptop, and it just stopped working all together, no program will work.
I've tried a few tweaks but nothing seems to affect it.

lspci | grep -i audio
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

---

### Post by Sunn3K7aas on 2008-01-30
Another person with almost the same problem. I have a Sony Vaio VGN-T250P laptop, with an Intel 82801DB-ICH4 sound chip. Ever since I installed Kubuntu 7.10 on this laptop, the sound hasn't worked. Everything seems to be ok. The system recognizes the sound chip and the correct modules seem to loaded into the kernel. All the output from lspci and aplay -l seem to be fine as well. Nothing I can find seems to be out of order. There's just no sound output. It could be something wrong with arts but I don't know enough about it to find out if something is wrong.

---

### Post by c_07 on 2008-01-30
Exactly the same symptoms here... VERY frustrating, as I must record screencasts for school :(

```
$ lspci | grep -i "audio"
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

**_Edit_**
After working for hours on this problem, my sound mysteriously started working! It was just after I followed the _[COLOR="Blue"]["Getting the ALSA drivers from a *fresh* kernel"]("http://ubuntuforums.org/showthread.php?t=205449")[/COLOR]_ steps, compiling the **snd-hda-intel** manually. The strange thing is, the sound started working not after the first reboot, but after a couple! :confused:

I also appended this line to the end of /etc/modprobe.d/alsa-base:
```
options snd-hda-intel model=lg
```
...but I did that a while back, and I don't know if it is related to the solution or not.

Basically, I've tried so many different things today I have no idea if it was due to a combination of a bunch of accidents. At least my sound is working for the time being...

**_Edit #2_**
I finally got it working! It was a matter of playing around with alsamixer's options... I've attached a screenshot of my configuration. The funny thing is, and the reason I didn't try this configuration before, is that I am using an **external** mic, but I had to enable the internal mic to allow recording. :)

---

### Post by Tiekyl on 2008-01-30
I am also having the same problems, it just started about an hour ago. I muted the sound and when I came back, I couldn't get it to come up anymore. 

This is what I have on my hardware: 
```
katie@Fluffy:~$ lspci | grep -i "audio"
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

When I try to change the sound event playback to ESD, I get ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server
```

When I try to change it to OSS, I get ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.
```

Also, it is the same on Debian Etch, as a matter of fact, thats where it started. The sound started up one time when I was logging into XFCE, or at least I heard the startup sound play through my headphones. (Just trying to give more information, in case it helps. )

---

### Post by newhope16 on 2008-01-30
i have zero sound as well....

all alsa drivers etc up to date... sound card is detected & default....

i pass all the sound checks from the sound troubleshooting topic....

yet no sound plays.... ive been banging my head against a desk for 3 days trying to fix this....

---

### Post by david on 2008-01-31
I had the same problem on my Lenovo R60 laptop which have a Intel ICH7 sound card.  It has three buttons:  **mute** and** volume up** and **volume down.** and it was these that screwed things up.

Pressing **mute** and then **volume up**  a couple of times it started working again. btw if I mute the sound by the **mute** button I can't unmute it from anything but the **volume up** button,*not* even alsamixer!

---

### Post by gwpritch on 2008-01-31
This seems to be a huge problem for anyone with sound cards requiring the hda-intel alsa module. I had the same problem and after trying all the easy fixes suggested in various forum posts I finally fixed it by compiling the latest version of alsa:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

It was some time ago, and I had one or two false starts compiling alsa-driver.  If I remember right it had something to do with the line:

```
./configure --with-cards=hda-intel
```

before proceeding use:

```
./configure --help
```

to view your options and check the syntax. I think I added in a --with-codecs or somesuch. 

Sorry I can't be more specific but I was doing all this by the seat of my pants.

Hope it helps. Good Luck.

---

### Post by iiinked on 2008-01-31
> **gwpritch said:**
> This seems to be a huge problem for anyone with sound cards requiring the hda-intel alsa module. I had the same problem and after trying all the easy fixes suggested in various forum posts I finally fixed it by compiling the latest version of alsa:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

It was some time ago, and I had one or two false starts compiling alsa-driver.  If I remember right it had something to do with the line:

```
./configure --with-cards=hda-intel
```

before proceeding use:

```
./configure --help
```

to view your options and check the syntax. I think I added in a --with-codecs or somesuch. 

Sorry I can't be more specific but I was doing all this by the seat of my pants.

Hope it helps. Good Luck.

Thank you so much. This worked for me. The linked HOWTO was wonderfully easy to follow and fixed the problem quickly. I cannot thank you enough for showing this to me and restoring my computer to it's former luster!

---

### Post by henrikbrink on 2008-01-31
Me too, wuhuuuu!

Im just sure I tried this before, but who cares, this thing works! 

Thank you very much!

---

