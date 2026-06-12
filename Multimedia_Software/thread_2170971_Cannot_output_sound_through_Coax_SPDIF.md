---
title: "Cannot output sound through Coax S/PDIF"
date: 2013-08-28
forum: Multimedia Software
---

### Post by hornets365 on 2013-08-28
Hi there,

Right now I am trying to get my Koss 5.1 surround sound system working with Ubunt 13.04 64 bit.  I know it works because I am able to use it on Windows 7 and with my TV.

I have searched around but cannot seem to find anything that will let me output through the Coax S/PDIF on my motherboard (HP Berkeley with a q6600).  I do not have a PCI sound card, only integrated audio.  

Even through pavucontrol I can't select digital output.  I have also tried reinstalling Alsa and Pulseaudio to no avail.

Can someone help me?

EDIT: Normal analogue speakers work fine

---

### Post by tgalati4 on 2013-08-28
What module is loaded for your sound card?

```
lsmod | grep snd
modinfo snd_hda_intel
```

*modinfo* will give you the switches available for the module that you have loaded.  No switch means no capability for that feature.

---

### Post by Yellow Pasque on 2013-08-28
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by hornets365 on 2013-08-28
I guess this is what you wanted:

```
http://www.alsa-project.org/db/?f=bd8f7855f6188d6e60b3c0949d3aa3c86525799f
```

---

### Post by hornets365 on 2013-08-28
Here is what I got back in the terminal: 

```
jimmy@JUbuntu:~$ lsmod | grep snd
jimmy@JUbuntu:~$ modinfo snd_hda_intel
ERROR: Module snd_hda_intel not found.

```

---

### Post by tgalati4 on 2013-08-29
How about:

```
lsmod
```

---

