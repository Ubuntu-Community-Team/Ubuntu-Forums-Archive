---
title: "projectM working in 8.04?"
date: 2008-05-01
forum: Mythbuntu
---

### Post by castles on 2008-05-01
I've been trying to get projectM working in Mythbuntu Hardy. I installed from the repository and it shows up in mythtv settings but when I try and playback music with the visualizer on I just get a white screen. When I try and exit the visualisation I get a segmentation fault.

I followed this guide.. [http://ubuntuforums.org/showthread.php?t=749793]("http://ubuntuforums.org/showthread.php?t=749793") and managed to compile projectM from source. The test seems to run (projectM-test) but I get this error when trying to run projectM (projectM-pulseaudio) in terminal:

```
Connection failure: Connection refused
ASSERT failure in QCoreApplication::sendEvent: "Cannot send events to objects owned by a different thread. Current thread 808ea78. Receiver 'QProjectM_MainWindow' (of type 'QWidget') was created in thread 8064118", file kernel/qcoreapplication.cpp, line 274
Aborted
```

It works on my other gnome Ubuntu computer so I was thinking it might be a xfce problem?

---

### Post by superm1 on 2008-05-02
When you start it on a terminal, are you starting it on a terminal on the "Xfce" session, or via ssh?  If the latter, you should try using the former instead.

---

### Post by castles on 2008-05-02
> **superm1 said:**
> When you start it on a terminal, are you starting it on a terminal on the "Xfce" session, or via ssh?  If the latter, you should try using the former instead.

I've been trying it in Xfce session.

---

### Post by plafuro on 2008-05-04
I experience the same problem. Funny enough the first time I run it it worked properly and latter on I got exactly that same message,

---

### Post by superm1 on 2008-05-04
I'm not familiar with projectM personally, but it sounds like perhaps a daemon is being spawned that isn't killing it off?

---

