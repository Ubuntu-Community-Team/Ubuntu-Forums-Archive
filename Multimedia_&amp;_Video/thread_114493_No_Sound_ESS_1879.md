---
title: "No Sound ESS 1879"
date: 2006-01-08
forum: Multimedia &amp; Video
---

### Post by wukkkie on 2006-01-08
I have install Ubuntu on a Compaq Armada 7400 Notebook and there is no sound, it looks like the soundcard is not detected. Somebody know how to fix it?

---

### Post by FarEast on 2006-01-08
Please have a try;) 
Describe the following in /etc/modprobe.d/sound .

```
options snd-es18xx enable=1 isapnp=0 port=0x220 \
mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0
```

```
$ sudo update-modules
$ sudo modprobe [COLOR="Red"]snd-[/COLOR]es18xx
$ alsamixer
```

I also point you to the thread:

[http://www.ubuntuforums.org/showthread.php?t=12525&page=2&highlight=es18xx](http://www.ubuntuforums.org/showthread.php?t=12525&page=2&highlight=es18xx)

---

### Post by wukkkie on 2006-01-09
Thanks FarEast....It works :p

---

### Post by FarEast on 2006-01-09
Hi wukkkie,

Glad that I could help you:p .

For corrent package of alsa-utils does not provide the script
'alsaconf', those who have ISA sound cards have have to do
this manually.

If it were available, they would be able to setup sound cards
easily...

---

### Post by wukkkie on 2006-01-15
In the control panel i see:
0: ESS Audiodrive ES 1879 (Alsa Mixer)
1: ESS Audiodrive ES 1879 (Oss Mixer)

When the notebook awake from sleepmode the sound is gone, when i click the sound button the notebook wil freeze. How can  i delete the Oss Mixer to see if this cause the freeze?

---

### Post by FarEast on 2006-01-15
Hi wukkkie;) 

Is 'snd-mixer-oss' loaded?
If the issue has something to do with the module, listing it in
'/etc/hotplug/blacklist' will be help.  Please try!

---

### Post by wukkkie on 2006-01-15
I think it is loaded, because i can switch between Alsa and OSS.
/etc/hotplug/blacklist i see only 3 files: alsa-base, libsane and linux-sound-base_noOSS. I try to understand but i don't get it :(

---

### Post by FarEast on 2006-01-15
> /etc/hotplug/blacklist i see only 3 files:
> alsa-base, libsane and linux-sound-base_noOSS.
> I try to understand but i don't get it

It is odd that alsa-base is listed in *blacklist*:confused: .

Which modules are loaded when your system comes back
from sleepmode?  Paste the out put of 'lsmod', please;) .

---

### Post by wukkkie on 2006-01-17
I can't see the lsmod after the sleepmode, because when i start it Ubuntu will freeze :(

---

### Post by FarEast on 2006-01-17
Hi,

> I can't see the lsmod after the sleepmode, because when i start it
> Ubuntu will freeze

I recommend you to start new thread of this issue if there are no thread
regarding this;) .  It must have something to do with it that your system
has "two mixers" after waking up from sleep.

---

### Post by wukkkie on 2006-01-19
Oke, thankx for the help :cool:

---

### Post by FarEast on 2006-01-27
Hi wukkkie,

Sorry, I made a mistake in advising you...

I wrote 'modprobe es18xx' but I should write 'modprobe [COLOR="Red"]snd-es18xx[/COLOR]'.
This must have caused the problem that you had 2 mixers(Alsa/oss).

---

