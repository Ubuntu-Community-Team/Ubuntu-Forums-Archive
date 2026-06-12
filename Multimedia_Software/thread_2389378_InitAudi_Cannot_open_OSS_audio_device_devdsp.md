---
title: "InitAudi: Cannot open OSS audio device /dev/dsp"
date: 2018-04-16
forum: Multimedia Software
---

### Post by chakikou11 on 2018-04-16
Hello everybody, 

I'm working on speech recognition with HTK, and when I run HSLab I have this error message " InitAudi: Cannot open OSS audio device /dev/dsp" 

any help please ?

---

### Post by &amp;KyT$0P# on 2018-04-16
Does it work to run it with [FONT=Courier New]padsp[/FONT]?
(Refer to [FONT=Courier New]man padsp[/FONT] for more info)

If not, does installing [FONT=Courier New]osspd[/FONT] help? -
```
sudo apt-get install osspd
```

---

