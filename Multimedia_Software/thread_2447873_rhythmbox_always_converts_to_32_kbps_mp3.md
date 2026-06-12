---
title: "rhythmbox always converts to 32 kbps mp3"
date: 2020-07-27
forum: Multimedia Software
---

### Post by martingwb2 on 2020-07-27
Hi,
When defining the quality (kbps) for importing mp3 files in rhythmbox from a CD no matter which value I choose (mp3, CBR, 192, 320, ...) it always creates 32 kbps mp3 files.
Any suggestions where this can be modified? Using 3.4.4 on ubuntu 20.04
The output of "file" for such a file looks like this:
```
file abc.mp3
abc.mp3: Audio file with ID3 version 2.3.0, contains:MPEG ADTS, layer III, v1, 32 kbps, 44.1 kHz, JntStereo
```

Thank you,
Martin

---

### Post by Yellow Pasque on 2020-07-27
Is it this bug? [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1654733](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1654733)

In general, I would recommend avoiding GNOME apps for CD ripping (sound-juicer/brasero/rhythmbox).

---

### Post by speartip on 2020-07-28
I'd use an app that's specifically for ripping CDs. Asunder has always worked well for me. And it's easy to configure.

---

### Post by martingwb2 on 2020-07-28
AAArrrrrrgghhh, exactly the same thing with fre:ac !

---

