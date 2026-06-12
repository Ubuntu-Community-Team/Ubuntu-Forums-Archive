---
title: "wine with alsa-oss help"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by Mooie on 2006-08-21
I have the alsa-oss package installed, how do I tell wine to use that instead of normal oss, because when I run games with wine, I cant listen to music (using AmaroK, w/ engine set to alsa).  I can listen to music and play quake4, which uses alsa.

also, it would be nice to get cedega to work w/ aoss too...   thanks :D

---

### Post by tuxcantfly on 2006-08-21
don't use alsa-oss. instead, run winecfg, and under audio, select alsa

---

### Post by Mooie on 2006-08-21
I would prefer to use alsa with WoW, but that is the ONLY program it doesnt work with :confused: i'm not sure why...     whenever I play world of warcraft with alsa, everything has lots of static and a little of bad reverb...

any suggestions?  thanks:D

---

### Post by tuxcantfly on 2006-08-24
well, why don't you use the esd or artsd drivers?

---

### Post by Mooie on 2006-08-29
I use Kubuntu (kde) and I dont see anything that says artsd under config ](*,) 

lately wine has been crashing and trying to debug somthing when i run WoW, i guess i will reinstall wine and/or WoW later

---

### Post by zek725 on 2006-11-04
> **tuxcantfly said:**
> don't use alsa-oss. instead, run winecfg, and under audio, select alsa

I've installed Wine from the official Edgy repository.

```
sudo aptitude install wine
```

Installation went fine. However, clicking the AUDIO tab in winecfg returns this error.

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/zek/.kde/socket-warrior2.
can't create mcop directory
```

Edit:
> **Eliseo said:**
> Found the solution here!:
[http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f](http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f)

I just had to do this:
```
mkdir -pv $HOME/.kde/socket-$HOSTNAME 
```

And voila! No more crashing!

IT WORKED! No longer crashes but terminal outputs these lines:

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
/bin/sh: /usr/bin/esd: not found
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

```

**winecfg** tells me that there are no audio drivers installed/found in registry. It chose for me OSS. I think ALSA is more stable?

---

### Post by puppy on 2006-11-10
I'm using a very recent version of Wine (0.9.22 I think?) and under winecfg's sound tab there's no longer an ALSA option - there's only OSS :confused:  

Do I need to load extra libs or something to get an ALSA option under winecfg? (btw I do use ALSA system-wide so it's not as if only the OSS sound system is loaded...)

---

### Post by blubman on 2007-02-21
I'm re-opening this thread for other people running into problems here.

Using alsa with WoW is know to cause problems, because Wine will need to convert from DirectSound. This results in choppy sounds and in often greatly reduced framerates. Using oss solves this, but doesn't allow any other sound from the system.

You can use **SET SoundOutputSystem "*n*"** in *Config.wtf* in "~/.wine/c_drive/Program Files/World of Warcraft/WTF/" to select, well, the Sound Output System. ***n*** is "1" for *"System sound"* (sent to oss) and "2" for *DirectSound* (converted by Wine and sent to alsa).

Simply put, everybody's better of using oss. Use aoss if you really need to play other sound (like music) while playing.

---

### Post by blubman on 2007-02-21
> **Mooie said:**
> I have the alsa-oss package installed, how do I tell wine to use that instead of normal oss, because when I run games with wine, I cant listen to music (using AmaroK, w/ engine set to alsa).  I can listen to music and play quake4, which uses alsa.

also, it would be nice to get cedega to work w/ aoss too...   thanks :D

To finally awnser your question:
Start WoW with ***aoss wine WoW.exe***

---

