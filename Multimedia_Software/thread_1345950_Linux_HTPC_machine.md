---
title: "Linux HTPC machine"
date: 2009-12-04
forum: Multimedia Software
---

### Post by Nevakonaza on 2009-12-04
Hello,

Im setting up an older pc to use as an HTPC....thing is i would like to use Linux....ubuntu because its reliable.

Now according to Avermedia who makes my TV tuner,Its Linux ready...however because i lack knowledge of how to use Linux i dont realy understand how to get it to work?

This is what ive come across so far on Avermedia,s website.

[IMG]http://i18.photobucket.com/albums/b125/shaneathome/1cap.png[/IMG]

[IMG]http://i18.photobucket.com/albums/b125/shaneathome/infos.png[/IMG]

It seems ive got to install some "Kernel" or something and it makes it plug and play?

[http://www.avermedia.eu/avertv/uk/Support/Download.aspx?Type=APDriver&tab=APDriver&id=39](http://www.avermedia.eu/avertv/uk/Support/Download.aspx?Type=APDriver&tab=APDriver&id=39)

Could anyone please help me out...i appreciate it alot :P

---

### Post by Nevakonaza on 2009-12-05
Bump anyone?

---

### Post by algiux1 on 2009-12-05
just plug it in ,install kaffeine and scan for channels.

---

### Post by matt06 on 2009-12-06
> **Nevakonaza said:**
> It seems ive got to install some "Kernel" or something and it makes it plug and play?

"kernel" refers to the version of linux you are running.  To find this out you can open a terminal and type "uname -r" like such:

```
matt@mythtv:~$ uname -r
2.6.31-15-generic
```

The AVerMedia site says that the driver is included if you have kernel 2.6.28 or higher.  To make the card "work" you'll need some type of capture/tuning software.

---

