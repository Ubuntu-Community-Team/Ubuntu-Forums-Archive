---
title: "Xubuntu - Wine Audio problem"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by JHe on 2006-09-01
Hello all;

I'm trying to configure Wine and it keeps on crashing whenever I press the audio tab. My terminal window shows:

Creating link /home/user/.kde/socket-audiohost.
Can't create mcop directory

My soundcard is an Intel AC97, module name Intel8x0

Otherwise, wine runs windows programs fine.

Thanks

---

### Post by shirilover on 2006-09-01
simple solution is to create the following directory--
~/.kde/socket-(computer name)
where (computer name) is the hostname you chose on setup.

---

### Post by JHe on 2006-09-01
Hmmm, I tried it but it didn't have an effect.

---

### Post by GeBo on 2006-11-18
Of course, after adding the path, run winecfg and select the appropriate audio source.

---

