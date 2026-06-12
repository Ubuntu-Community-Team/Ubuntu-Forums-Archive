---
title: "FATAL: Module snd_ not found."
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by addisor on 2008-02-15
My SPDIF sound has packed up after attempting a kernel patch and now whilst following the sound guide this happens

rob@rob-desktop:~$ sudo modprobe snd-
FATAL: Module snd_ not found.
rob@rob-desktop:~$ 

Any suggestions on how to reinstall snd

---

### Post by addisor on 2008-02-15
Now realise I made a simple error, should have typed

sudo modprobe snd-hda-intel

---

