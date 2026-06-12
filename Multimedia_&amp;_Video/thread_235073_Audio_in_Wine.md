---
title: "Audio in Wine"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by TheEmb3rEgg on 2006-08-12
I recently installed wine via automatix on my PC. When I open up winecfg and click the audio tab winecfg quits out and I get the following message in my terminal

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/timmy/.kde/socket-timmy2.
can't create mcop directory

I think the creating link error might have something to do with me installing the kubuntu-desktop last night.

I got the ALSA lib problem even before I installed kubuntu.

---

### Post by TheEmb3rEgg on 2006-08-12
Anyone have any ideas?

---

### Post by TheEmb3rEgg on 2006-08-12
I got rid of the creating link problem by loading into kubuntu and running winecfg. 

When i start winecfg I immediatly recieve this line in the terminal, but winecfg still loads up
```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

When I try to access the audo tab at the top of winecfg, I receive the following messege in the terminal.
```
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
```

Does anybody know to what ilbrary it is refering to?

---

### Post by erthian on 2006-11-19
> **TheEmb3rEgg said:**
> I got rid of the creating link problem by loading into kubuntu and running winecfg. 

When i start winecfg I immediatly recieve this line in the terminal, but winecfg still loads up
```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

When I try to access the audo tab at the top of winecfg, I receive the following messege in the terminal.
```
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
```

Does anybody know to what ilbrary it is refering to?

I was having the same problem, and every time I would run wine, it would lock down the audio and only work for any app running in wine...

Anny way, I just created the directory it couldnt fine, and that seemed to fix it.  I think it was looking for some thing that didn't exist, so it just failed and errored out.

Hope that helps.

---

