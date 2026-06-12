---
title: "How to make mp3blaster work in Maverick Meerkat?"
date: 2010-10-15
forum: Multimedia Software
---

### Post by Linfreak on 2010-10-15
Hi all,

       All of a sudden, I just had the idea of going back to command line music players and mp3blaster is what that came to my mind. I am running Kubuntu 10.10 on a Thinkpad T43 laptop with the default kernel. In an archived thread I read 

mp3blaster -s /dev/dsp 

would do the trick. But since all sound devices in my current laptop seem to be listed under /dev/snd as pcmC0D0p etc. I tried using,

mp3blaster -s /dev/snd/pcmC0D0p

and this gave a sound device control error.

Just did some digging around and saw that I didn't have any oss modules running. Are they the culprits? If not how would I make mp3blaster use my current devices else do I need to reconfigure my kernel to have the oss modules?

Thanks in advance,
Siva

---

### Post by daniffig on 2010-10-19
I had the same problem and this solution worked for me.

In a console window, write down.

```
modprobe snd-pcm-oss
```Then run mp3blaster this way.

```
mp3blaster -s /dev/dsp
```

---

### Post by Linfreak on 2010-10-22
First of all thanks for the effort daniffig. I tried your step but I am getting this error.

$sudo modprobe snd-pcm-oss
FATAL: Module snd_pcm_oss not found.

And I checked /boot/config-2.6.35-22-generic file to see if the SND_PCM_OSS kernel config value is set to m. But its not :(
Also SND_SEQUENCER_OSS and SND_MIXER_OSS are not set by default.

Does this mean I have no other go but to recompile my kernel or is there an easier way?

Thanks in advance,
Siva

---

### Post by Kyentei on 2010-11-09
You have to install alsa-oss
```
apt-get install alsa-oss
```
Then try this again.

---

### Post by Kyentei on 2010-11-09
Hm, nevermind I suppose. Mp3blaster depends on /dev/dsp which was removed since Ubuntu 10.10.

More info here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634211)

---

### Post by Kyentei on 2010-11-09
**Solution!**
If you run mp3blaster within padsp, it will work!
```
padsp mp3blaster
```

---

### Post by Linfreak on 2010-11-09
Thanks a ton Kyentei!! It works! But have you tried changing the volume? < > keys don't seem to work when started with padsp. It would be perfect if we can have volume control working too..

Cheers,
Siva

---

### Post by Yellow Pasque on 2010-11-09
Set mp3blaster to use the SDL AudioDriver in its config file and make sure libsdl1.2debian-pulse package is installed. Maybe volume keys will work then, since you won't have to use padsp/OSS.

---

### Post by Linfreak on 2010-11-09
When I added the 'AudioDriver = sdl' entry to ~/.mp3blasterrc file (libsdl1.2debian-pulseaudio is installed), and started mp3blaster, it gave the following error.

>> In config file, line 0001: Bad Value

Do I need to install something else too for this to work?

Thanks.

---

### Post by Kyentei on 2010-11-09
Sounds like we got this going again. And no clue on the volume by the way. You can always use alsamixer / aumix for that ^.^ (of course, just as alternative).

I wonder, has/have the mp3blaster developer(s) been informed about this yet?

Edit: Same issue here by the way, it won't read AudioDriver = sdl in my ~/.mp3blasterrc file either.


Edit2: Also, it seems that once mp3blaster finishes playing a song while loaded with the padsp thing, it does not hop to the following song in the list.

---

### Post by Bacchante on 2011-04-14
I am having the exact same problems here, done all the things said here, and the best my Debian system came up with is a full-volume track playing with '<' and '>' buttons are not working to alter the volume.

---

### Post by JanusDC on 2011-05-26
Any better solution since the last post?

I have this working with padsp, and everything work perfectly (after one song, it starts the following), the only problem I have is about the volume control. Anyway, is not that bad since I use it in a console in Genome (so I can use the keybindings from Gnome), but it would be nice to find a solution for it.

Cheers.

PS: I am using Natty (Ubuntu 11.04)

---

