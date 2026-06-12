---
title: "media players crash when playing video"
date: 2009-03-20
forum: Multimedia Software
---

### Post by zieglerj on 2009-03-20
I just switched from hardy to ubuntu studio and for some reason, no matter which media player I use, all of them either suddenly close or freeze the entire system when I try to watch videos. 
I'm sure I've got the right codecs. I could really use some help on this one.

---

### Post by mastermindg on 2009-03-20
The best way to resolve this is to open these applications in a terminal and monitor the output. If it closes you'll see the fault and if it freezes the system, you'll have plenty of time to view the last output lines :popcorn:

---

### Post by zieglerj on 2009-03-20
The readout when totem closed was: 

Segmentation fault

---

### Post by zieglerj on 2009-03-21
I did a fresh install of just hardy and it's still doing it. I'm running a 64 bit system with a 2ghtz AMD processor and NVIDIA video card with the manually installed driver.

---

### Post by zieglerj on 2009-03-21
Did a completely fresh install of intrepid and didn't make any changes other than installing the NVIDIA driver and the codecs needed to play .avi. Still having the same problem except now every once in a while instead of just freezing or crashing the xserv restarts leaving me at the login screen.

---

### Post by zieglerj on 2009-03-22
Problem seems to be fixed when I did a fresh install of intrepid and then activated the "pre-release updates" and "unsupported updates" from the updates tab of software sources and intalled all of the updates.

---

