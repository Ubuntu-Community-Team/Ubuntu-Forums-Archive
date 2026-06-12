---
title: "No sound intel-hd even after upgrading to ALSA 1.0.19"
date: 2009-01-31
forum: Multimedia Software
---

### Post by Dirob on 2009-01-31
I have been trying for days to get the sound on my xxodd (=mitac??) 8227 laptop working. I searched all forums, tried a lot of tricks, but nothing really worked. After I installed the upgrade of alsa, finally my soundcard was recognized, but did not work when I tested it on System>Preferences>Sound.
I even reinstalled ubuntu and tried everything again.
Last week I tried to install OSS, then I had some sound, but not in every application.
Can someone give me advice.
This is the result of running alsa-info:
[http://www.alsa-project.org/db/?f=3bd9e00be62e66850b1d6e57dc81b9da64756cb6](http://www.alsa-project.org/db/?f=3bd9e00be62e66850b1d6e57dc81b9da64756cb6)

Thanks,
Robin

---

### Post by linux_tech on 2009-01-31
what is output of :
```

cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by Dirob on 2009-01-31
I just got some sound out of my laptop!
I found it here:
[http://mysettopbox.tv/phpBB2/viewtopic.php?t=18596&sid=70165535e324e0e177baaf20f53feb51](http://mysettopbox.tv/phpBB2/viewtopic.php?t=18596&sid=70165535e324e0e177baaf20f53feb51)

I just added 

options snd-hda-intel model=medion

to the result of
```
sudo gedit /etc/modprobe.d/alsa-base

```
It worked, but the sound is not very loud...
So I think I will look for a solution for this myself, or you must have a good idea! 
These are the results from the terminal, but I don't think it will matter now?!

Codec: Realtek ALC883
Codec: Conexant ID 2c06
Codec: Realtek ALC268

Thanks

---

### Post by linux_tech on 2009-01-31
glad to hear its working

---

