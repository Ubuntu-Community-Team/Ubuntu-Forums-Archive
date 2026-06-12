---
title: "using vcdimager/vcdxrip to copy .DAT files"
date: 2008-08-06
forum: Multimedia Software
---

### Post by sharad.sharma on 2008-08-06
I can mount VCDs on Ubuntu 8.04 but can neither play the .DAT files nor copy them on the hard drive.How can I do that ?
I was looking for the solution and found that I need to install vcdimager package and then use the vcdxrip command to copy the .DAT file but I wasn't able to do that.Probably,I'm not doing it the right way.Please help.

I can't install w32codecs either.What is the alternative?

Thanks

---

### Post by sharad.sharma on 2008-08-06
I can mount VCDs on Ubuntu 8.04 but can neither play the .DAT files nor copy them on the hard drive.How can I do that ?
I was looking for the solution and found that I need to install vcdimager package and then use the vcdxrip command to copy the .DAT file but I wasn't able to do that.Probably,I'm not doing it the right way.Please help.

I can't install w32codecs either.What is the alternative?

Thanks

---

### Post by sharad.sharma on 2008-08-07
Please help. I tried gxine too but haven't been able play to DAT files.

---

### Post by shirilover on 2008-08-07
Have you configured xine to look for a video-cd at the location you mounted it to?
Then, try using 
```

xine vcd://1

```
which should play the first track on the video-cd

---

### Post by sharad.sharma on 2008-08-08
Thanks! :)

---

