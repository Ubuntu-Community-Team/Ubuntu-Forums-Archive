---
title: "[SOLVED] Upgrate to Gutsy 7.10 broke my Nvidia driver"
date: 2008-05-10
forum: Multimedia Software
---

### Post by Beatbreaker on 2008-05-10
how can i fix this? i'm getting an error saying that i've got one driver installed, but my system is looking for a different version driver and it then simply dumps me in the terminal upon bootup 

is this the solution?

[http://ubuntuforums.org/showthread.php?p=3018722#post3018722](http://ubuntuforums.org/showthread.php?p=3018722#post3018722)

---

### Post by Seks on 2008-05-10
try 

sudo apt-get update nvidia-glx-new

(or nvidia-glx, or nvidia-glx-legacy based of your current driver)

---

### Post by Beatbreaker on 2008-05-19
> **Seks said:**
> try 

sudo apt-get update nvidia-glx-new

(or nvidia-glx, or nvidia-glx-legacy based of your current driver)

How do i find out my current driver? It's been a long time since i played with this, i think the standard driver seemed to work ok though.

---

### Post by Beatbreaker on 2008-05-19
the command dosen't work

sudo apt-get update nvidia-glx-new

nvidia-glx doesn't work either, i doubt i've got a legacy driver

how do i solve this, what's the command?

---

### Post by Beatbreaker on 2008-05-19
Bump

Can anyone help with this one? i've forgotten a lot of the commands that i used to know. Do you need any more information? I will try my best to fill you in.

---

### Post by Beatbreaker on 2008-05-20
i used this command 

> sudo dpkg-reconfigure xserver-xorg

and now i have an xserver error that says

(EE) NV(0) No display devices found
(EE) Screen(s) found but none have....(something i forgot)

help

---

### Post by Beatbreaker on 2008-05-22
...what's happened to the forums here? People used to be so helpful. Is the popularity of Ubuntu waning?

---

### Post by Xiong Chiamiov on 2008-05-22
> **Seks said:**
> try 

sudo apt-get update nvidia-glx-new

(or nvidia-glx, or nvidia-glx-legacy based of your current driver)
That should actually be apt-get install, rather than apt-get update.  If you have problems, you can also try [installing them manually]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329").

There has been quite an influx of traffic with the release of Hardy, and it seems most people are focused on the Absolute Beginner forum, since it's *incredibly* high-traffic and arguably the most important.

---

### Post by Beatbreaker on 2008-05-26
Resolved - I decided not bother trying to fix the broken update and installed Hardy over the top instead. I gotta say i'm VERY impressed. I was worried but i tested the hardest things and they all work now, my web cam - Perfect. My printer, worked after plugging it in. It was TOO easy!!!

Great work guys!

---

