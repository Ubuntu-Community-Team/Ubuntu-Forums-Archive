---
title: "Error when compiling v4l-dvb - snd_card_create"
date: 2009-09-14
forum: Mythbuntu
---

### Post by icevapor on 2009-09-14
Hey all,

I have a Mythbuntu 8.10 system w/ a pctv 800i (pci card) and a pctv hd stick (800e).  Had both running just fine for about 8 months... then the stick stopped working.  It works but wont pick up a signal.

I decided I would update my system a little and figure out what broke my 800e.  I updated my kernel and went to recompile v4l-dvb and got this error:

```
  CC [M]  /home/mythbox/Firmware/v4l-dvb/v4l/snd-go7007.o

/home/mythbox/Firmware/v4l-dvb/v4l/snd-go7007.c: In function 'go7007_snd_init':

/home/mythbox/Firmware/v4l-dvb/v4l/snd-go7007.c:251: error: implicit declaration of function 'snd_card_create'

make[3]: *** [/home/mythbox/Firmware/v4l-dvb/v4l/snd-go7007.o] Error 1

make[2]: *** [_module_/home/mythbox/Firmware/v4l-dvb/v4l] Error 2

make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'

make[1]: *** [default] Error 2

make[1]: Leaving directory `/home/mythbox/Firmware/v4l-dvb/v4l'

make: *** [all] Error 2 
```

I was using the old copy of v4l I had so I thought it might have been the new kernel fighting w/ the old v4l.  So I updated v4l... same error.  

I dinked w/ it for a long time and finally gave up and upgraded to 9.0.4.  Same error, now neither of my cards will work (brutal!). 

I dont even know what the snd-go7007 would go with... I dont even have that type of hardware (i dont think).

Anyone have any ideas?

---

