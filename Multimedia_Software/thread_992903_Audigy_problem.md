---
title: "Audigy problem"
date: 2008-11-25
forum: Multimedia Software
---

### Post by provolone25 on 2008-11-25
I'm using  Creative Labs SB Audigy but sounds does not work; so i followed this thread on the forums: Comprehensive Sound Problem Solutions Guide.
I tryed to compile alsa from source but i get this error:
```
/usr/src/modules/alsa-driver/acore/sound.c: In function ‘snd_request_other’:
/usr/src/modules/alsa-driver/acore/sound.c:100: warning: format not a string literal and no format arguments
  CC [M]  /usr/src/modules/alsa-driver/acore/init.o
/usr/src/modules/alsa-driver/acore/init.c: In function ‘snd_card_register’:
/usr/src/modules/alsa-driver/acore/init.c:568: warning: passing argument 5 of ‘device_create’ makes pointer from integer without a cast
/usr/src/modules/alsa-driver/acore/init.c:568: warning: format not a string literal and no format arguments
  CC [M]  /usr/src/modules/alsa-driver/acore/memory.o
  CC [M]  /usr/src/modules/alsa-driver/acore/info.o
/usr/src/modules/alsa-driver/acore/info.c: In function ‘resize_info_buffer’:
/usr/src/modules/alsa-driver/acore/info.c:90: error: implicit declaration of function ‘PAGE_ALIGN’
make[3]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [compile] Error 2

```

I already tryed using the driver from apt but without success and loading driver manually but aplay show no cards :) Some1 can help me?

---

### Post by AllenGG on 2008-11-25
When you use "aplay -l" you should, at least, get the onboard sound . What happens with "lspci" ?

---

### Post by provolone25 on 2008-11-25
this is theoutput of lspci:
```
00:0e.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs Device 0040
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at d800 [size=32]
	Capabilities: <access denied>
```

aplay -l tell me that there is no device

---

### Post by AllenGG on 2008-11-25
So, HAL, I believe , sees the card .  Go in to Synaptic.  Search "sound" using "name and description".
You should see "ALSA"  packages loaded. I have at least 12 on my system. It appears that on my system that "alsa-firmware-loaders" is the most essential to recognize and load my CreativeSB Live 5.1 card.

---

### Post by provolone25 on 2008-11-25
that package was not installed on the system, so i installed it and load the driver but doesnt help

---

### Post by AllenGG on 2008-11-25
See if "PulseAudio" is installed on your system, easiest way, check through Synaptic.
Go back to alsa and look at recommended packages and suggested packages.

---

### Post by provolone25 on 2008-11-25
All packages are installed but dont know whats the problem :S

---

### Post by AllenGG on 2008-11-25
Possibly a "Pulseaudio" problem. Look here: [http://ubuntuforums.org/showthread.php?t=789578&highlight=skype+sound](http://ubuntuforums.org/showthread.php?t=789578&highlight=skype+sound).
I needed to change my "software sources" to get Pulseaudio to work properly (like "play nice in the sandbox).
Release upgrade to :"normal". Reload package info. Please note that I have all of the Medibuntu repositories  made active. see:
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

---

### Post by provolone25 on 2008-11-26
I read the guide u post :) Some libs was not installed but the problem is that even if i load the module of the sound card system doesnt recognize it

---

### Post by provolone25 on 2008-11-26
This morning im trying to compile again the alsa driver from apt alsa-source and i read the SUPPORTED_KERNEL file:
```
The alsa-drivers in this package are designed for the following kernels:

 - Vanilla 2.6.25 or earlier
 - Vanilla 2.4.31 or earlier
 - Vanilla 2.2.26 or earlier

It's not guaranteed that they work with any newer version than above
or modified kernels by distributors.

```

ubuntu intrepid is using 2.6.27 kernel so alsa-1.0.17 should not be compatible or not? :D

---

### Post by mc4man on 2008-11-26
you may want to try something simple that may or may not work.

double left click on the little speaker icon in upper panel. A box should pop up and if there is a 'switches' tab open it and change whatever it it set to to the opposite, if the box is checked then uncheck it, if it's unchecked, then check it.

---

### Post by provolone25 on 2008-11-26
Do u mean pulse audio icons? If so i cant do nothing there is no device

---

### Post by provolone25 on 2008-11-26
Problem solved; im using alsa driver, libs and utils from source :)

---

