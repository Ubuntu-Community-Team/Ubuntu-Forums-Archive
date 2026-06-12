---
title: "OSS anoyance"
date: 2006-06-30
forum: Multimedia &amp; Video
---

### Post by Sheik Yerbouti on 2006-06-30
I have two soundcards in my system Audigy 2 and M-Audio Delta 66. And I have the setup working fine in general I even succesfully have the Audigy 2 using the Delta 66 as output via SPDIF. 

There is one anoyance though and maybe someone knows an answer. When I reboot into the RT kernel or back to the stock ubuntu kerenel again OSS seems to make the Audigy /dev/dsp and the Delta 66 /dev/dsp1 one time and then the next time it makes the Delta 66 /dev/dsp and the Audigy 2 /dev/dsp1. It doesn't even seem very consistent. Is there a way to force the kernel modules to load in a specific order so that one is always /dev/dsp and the other /dev/dsp1 like in /etc/modules or something. Alsa does not munge them like that by the way.

Cheers

---

### Post by Sheik Yerbouti on 2006-07-01
I think I now have this sorted. I guess it's not really OSS it's some sort of alsa OSS compatibility layer. I guess you can't really have both Alsa and OSS kernel modules loaded at the same time but I am not totally sure on that. At any rate I believe it was an alsa problem that was showing up through the OSS compatibility layer.

This page [http://alsa.opensrc.org/index.php?page=MultipleCards](http://alsa.opensrc.org/index.php?page=MultipleCards) was very helpful in my understanding as was reading the comments in /etc/modprobe.d/alsa-base. This is the change I made I added two lines into /etc/modprobe.d/alsa-base and it seems to have straightened things out. 

```
options snd-emu10k1 index=0 
options snd-ice1712 index=1
```

the first line forces the Audigy 2 to be card 0 or /dev/dsp in OSS parlance and the second line forces the Delta 66 to be card 1 or /dev/dsp1. After about four reboots between kernels to test it seems to be working. Hope this may help someone else.

---

