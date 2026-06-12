---
title: "I need an Avi to wmv converter"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by BerCapone on 2007-12-17
Can someone help me becouse i need to convert some videos from avi to wmv, to put those on my philis gogear

---

### Post by Rhubarb on 2007-12-18
Mencoder can export to wmv1 (the quality isn't that good, but try it for yourself to see).
```
mencoder -ovc lavc -lavcopts vcodec=wmv1:vbitrate=800 -oac pcm -o ./output.wmv input.avi
```

---

### Post by Lostincyberspace on 2007-12-18
I use mencoder. But there is Iriverter in the repository's that has a gui, but I don't know if it will convert to wmv.

---

### Post by BerCapone on 2007-12-18
memcoder doesent works. it gives me :

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
File not found: 'input.avi'
Failed to open input.avi.
Cannot open file/device.

                  i tell you i´m a completly amature

---

### Post by BerCapone on 2007-12-18
and amiersoft has an exe file 
    it woks on windows not?

---

### Post by KCPokes on 2007-12-18
> **BerCapone said:**
> memcoder doesent works. it gives me :

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
File not found: 'input.avi'
Failed to open input.avi.
Cannot open file/device.

                  i tell you i´m a completly amature

Is the file you are trying to convert named input.avi?  The line provided was just an example, thus you'll need to input your filename where input.avi is in the command.  Keep in mind that you'll need to be in the same directory as the avi, or use absolute path to the file.

---

### Post by ron999 on 2007-12-19
**seashell** and **videolovely** are damn spammers, look at their other posts.

---

### Post by frodon on 2007-12-19
Use the "report " button next time so we are informed quickly, they are both banned now.

thanks.

---

