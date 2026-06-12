---
title: "No webcam driver"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by ftpaddict on 2007-06-23
[Extreme n00b warning]

I've got a Gembird 44u webcam and no drivers for Linux. :(
Any requests for a Linux driver on the official forum have been left unanswered.

The camera itself uses a ViMicro 305b chipset, if it helps...

Sadly, the prospect of buying a new webcam in the foreseeable future is very slim.

Can anyone please help? :cry:

---

### Post by nalmeth on 2007-06-23
Have you googled 'ubuntu webcam' ?

The second page in the results is this one:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

I don't know if your webcam will work right away like mine did, but this is where you should start.

---

### Post by ftpaddict on 2007-06-24
It didn't work, unfortunately. My webcam model is not supported by the application. :(

---

### Post by chemtut on 2007-06-25
try either camorama or camstream----use synaptic

run camstream in a terminal-----good luck

---

### Post by ftpaddict on 2007-06-26
As far as I can tell, neither Camorama nor Camstream provide drivers for webcams. Their only purpose is to view webcam images.

---

### Post by dabl on 2007-06-26
Although the title refers to Logitech webcams, the basic issue of making a gspca driver for USB webcams is the same (you might be wise to start at the end of the thread, rather than the beginning):

[http://ubuntuforums.org/showthread.php?t=303330&highlight=how+to+webcam](http://ubuntuforums.org/showthread.php?t=303330&highlight=how+to+webcam)

It says here that Vimicro chips are supported, although I don't see your specific chip:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)


I'd try to make a gspca driver following the procedure in the first link -- doesn't sound like there's lots to lose.

:(

---

