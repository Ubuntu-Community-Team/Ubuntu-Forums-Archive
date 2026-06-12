---
title: "Sounds Doesn't Work"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by darkNiGHTS on 2007-11-08
For some reason all of the sound on my computer stopped working.  I am running Ubuntu 7.10 x64.  I have tried changing the devices in the sound preferences menu, but it still doesn't work.  Help would be appreciated.

Thanks

---

### Post by bhavin66 on 2007-11-09
Same here.
Was trying out Miro and then there was a system update which i did.
This morning got some error message " Device refusing to freeze....." and sound is gone

Tried this and found this really helpful. Dont know what would have caused it but found that volume was tuned all the way down.

[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+stopped](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+stopped)

---

### Post by darkNiGHTS on 2007-11-09
Thanks for the help, but for some reason that didn't work for me.  I tried recompiling the sound card and then when I do
```
coryr@coryr-desktop:~$ sudo modprobe snd-

```

It says this
```
coryr@coryr-desktop:~$ sudo modprobe snd-
FATAL: Module snd_ not found.

```

---

