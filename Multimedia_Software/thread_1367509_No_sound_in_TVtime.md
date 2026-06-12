---
title: "No sound in TVtime"
date: 2009-12-29
forum: Multimedia Software
---

### Post by Oldfield88 on 2009-12-29
Hi everyone,

I have a problem with my TVTime. I got the picture but not the sound. I have had the sounds up and running but it was through skype. so i coulnd't hear it myself but the one on skype did. Anyone got some help here? the card is a TVP103 from E-TECH. I see it also loaded when i run dmesg and no where to find the sound for it. Can anybody help me here?

Greetings old

---

### Post by buntunub on 2009-12-29
A 2 second Google search on this card revealed [this]("http://www.archivum.info/video4linux-list@redhat.com/2007-09/00036/Re:_E-Tech_TVP103:_Anyone_has_it_working") which basically points the fact that the card is recognized, but you will have to insmod the settings.

First, go in to a terminal and type

```
dmesg | grep saa
```

Because it looks like your card uses the saa driver via v4l2. You can also sub in your card name after the grep and see what you get. Eventually, after you figure out what your hardware info is, you should be able to insert a modprobe option to get the card up and running.

Create a file..

```
sudo gedit /etc/modprobe.d/saa7134
``` (or whatever your driver name is)

and then input your card and tuner options.

```
options card=? tuner=?
```

You have quite a lot of research and google searches ahead of you if you want to get the card working, so I will leave off at that. Keep in mind too that some cards do not list a tuner. Fun fun!

---

### Post by Uncle Spellbinder on 2009-12-30
Nevermind..................

---

### Post by Oldfield88 on 2009-12-30
Thanks going to try that. I'll let you know how it went.

> **buntunub said:**
> A 2 second Google search on this card revealed [this]("http://www.archivum.info/video4linux-list@redhat.com/2007-09/00036/Re:_E-Tech_TVP103:_Anyone_has_it_working") which basically points the fact that the card is recognized, but you will have to insmod the settings.

First, go in to a terminal and type

```
dmesg | grep saa
```Because it looks like your card uses the saa driver via v4l2. You can also sub in your card name after the grep and see what you get. Eventually, after you figure out what your hardware info is, you should be able to insert a modprobe option to get the card up and running.

Create a file..

```
sudo gedit /etc/modprobe.d/saa7134
``` (or whatever your driver name is)

and then input your card and tuner options.

```
options card=? tuner=?
```You have quite a lot of research and google searches ahead of you if you want to get the card working, so I will leave off at that. Keep in mind too that some cards do not list a tuner. Fun fun!

---

