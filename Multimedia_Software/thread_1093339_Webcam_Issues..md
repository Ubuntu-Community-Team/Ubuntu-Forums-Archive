---
title: "Webcam Issues."
date: 2009-03-11
forum: Multimedia Software
---

### Post by Ratscallion on 2009-03-11
Hi again. I am wanting to use my webcam on Ubuntu, for Skype, aMSN and Video Blogs. However, I have a slight problem. Does my webcam work, yes it does. Does it work properly, no. 
When I test it (with cheese) I get a blue/cyan background with a sort of negative cross heat vision picture. Basically, I can't see anything in good detail, it flickers a lot. Despite all this, the webcam LED (on) is on (blue). Please help me sort out these issues, as I wish to fulfill the above on Ubuntu. I know a bit about Ubuntu like commands in Terminals etc. Though please explain your code so I know how it works.

Ubuntu 8.10 Wubi.
HP G7094
Not sure what make the Webcam is, it's joined to the laptop.

---

### Post by cariboo on 2009-03-11
Could you open an Applications-->Accessories-->Terminal and type:

```
lsusb
```

and paste the output in your next post, this will help determine what what make your webcam is.

Jim

---

### Post by Ratscallion on 2009-03-11
Ok. However, I don't know if my Webcam is USB as it is non-removable (unless you know what you're doing. Anyway, heres the reply:

```
 
Bus 004 Device 004: ID 13fe:1c00 Kingston Technology Company Inc. 
Bus 004 Device 002: ID 064e:c108 Suyin Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```Does that help, most of it doesn't make much sense to me lol.

---

