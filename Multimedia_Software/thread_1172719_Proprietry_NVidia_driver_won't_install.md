---
title: "Proprietry NVidia driver won't install"
date: 2009-05-28
forum: Multimedia Software
---

### Post by j3ff on 2009-05-28
Hi,

I have recently upgraded my workstation to 9.04.  I am trying to enable the proprietry nvidia graphics card drivers (version 180) as I have an NVidia GeForce 8500 GT card installed.

System -> Administration -> Hardware Drivers  tells me about two versions of the nvidia driver, 173 and 180.  However, when I select one (either) and click "Activate" I get a small error dialog with no text on it, and the driver remains not installed.

Any help greatly appreciated.

Cheers,
Jeff

---

### Post by j3ff on 2009-05-29
OK, I seemed to have solved the problem, although I'm not sure exactly what fixed it.  I think it was restarting the jockey backend in debug mode.

I issued 

```
sudo killall jockey-backend
sudo /usr/share/jockey/jockey-backend --debug -l /tmp/jockey.log
```

It still didn't work.  It sat at 0% and then crashed, indicating that it would restart (jockey).  

The next attempt was successful.  I really don't know why.  I was hoping to get some insight from the log I asked jockey to generate, but instead it decided to work.  I got nothing from the previous crash.  Nothing was written to the log about that (I was observing it with tail -f).

I doubt that this post will help anyone, but I thought I'd at least indicate that I no longer have the problem.

---

