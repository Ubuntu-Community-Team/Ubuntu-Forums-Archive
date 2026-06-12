---
title: "Converting rm files to avi using mencoder - file size question."
date: 2009-11-19
forum: Multimedia Software
---

### Post by uncle-c on 2009-11-19
Hi,
I have a bunch of Real Media files which I would like to convert to avi format. I'm using a simple mencoder command to do this :

```

 $ mencoder 021.rm -oac mp3lame  -ovc lavc -lavcopts vcodec=mpeg4 -of avi 
-o sample.avi

```

The original .rm file is approx 10Mb in size but when I convert it to .avi it doubles in size to about 20Mb.  I was just wondering if this is standard or could I adjust the above code to make the resulting .avi slightly smaller in size ?

Thanks
C

---

### Post by benerivo on 2009-11-19
Try adding a vqscale value from 0 to 31. A value of 0 gives best quality video but largest file and 31 gives the lowest quality but smallest file. Add it in to your line like this```
$ mencoder 021.rm -oac mp3lame  -ovc lavc -lavcopts vcodec=mpeg4:vqscale=10 -of avi -o sample.avi
```

---

