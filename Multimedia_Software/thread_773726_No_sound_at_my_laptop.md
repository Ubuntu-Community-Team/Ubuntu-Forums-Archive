---
title: "No sound at my laptop"
date: 2008-04-29
forum: Multimedia Software
---

### Post by bibawa on 2008-04-29
Hello,

I've installed ubuntu and now i've no sound at my laptop, I've found a thread([http://ubuntuforums.org/showthread.php?t=205449&highlight=reinstall+alsamixer](http://ubuntuforums.org/showthread.php?t=205449&highlight=reinstall+alsamixer)) to reinstall alsa drivers from source, but nothing works.

When I start alsamixer in a shell the error he gives to me:

ALSA lib simple_none.c:1741:(simple_add1) helem (MIXER,'Headphone Playback Switch',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument


When I pres modprobe -snd and than TAB, there is nothing to modprobe.

What can I do?

---

### Post by litmos95 on 2008-04-29
try this:

```

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

```

and then reboot. If still no sound, set the sound to autodetect (System > Preferences > Sound)

---

### Post by bibawa on 2008-04-29
When I do that and then reboot he says "No sound card installed" :/

Also when i set it to autodetect..

---

### Post by litmos95 on 2008-04-29
So it might be the driver is missing. Have you tried Hardware Testing (System > Administration > Hardware Testing), it might give you some hints.

---

### Post by bibawa on 2008-04-29
Yesterday he said there that he detects a video card (Intel) but now there's no test for testing the audio :/ 

So I think at the moment he didn't detect any soundcard

---

### Post by litmos95 on 2008-04-29
Look whether you can find your sound card in
```

sudo lshw

```

---

### Post by bibawa on 2008-04-29
When I run that :

```

*-multimedia UNCLAIMED
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress cap_list
             configuration: latency=0


```

So the card is detected :/

---

