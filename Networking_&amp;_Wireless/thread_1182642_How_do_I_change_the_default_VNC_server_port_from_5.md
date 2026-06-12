---
title: "How do I change the default VNC server port from 5900 to something else?"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-06-09
I have my computer setup to accept incoming connections for VNC remote desktop sessions on 5900, which is the default for Ubuntu 9.04.  But I have just added another computer to my network and would like to use a separate port number to differentiate between the two PCs so I can vnc into each separately.  Is there a way to change the default port Ubuntu listens on for incoming connections?

---

### Post by sedawk on 2009-06-09
I just wanted to tell you how easy this is, when I found out that
Ubuntu does it differently then the Linux I use on my servers :o

So the only thing I can say for now is:
Can you run vncconfig and check if you can change the
port there from 5900 to 5901, 5902, ...
(Sorry, cannot test that here currently ...)

---

### Post by diablo75 on 2009-06-09
> **sedawk said:**
> So the only thing I can say for now is:
Can you run vncconfig and check if you can change the
port there from 5900 to 5901, 5902, ...
(Sorry, cannot test that here currently ...)

Aptitude (sudo apt-get install vncconfig) shows this to be a non-existent package.  Sorry, that didn't work for me.

---

### Post by sedawk on 2009-06-09
The tool "vncconfig" should be installed if you already have
vncserver installed. I think I installed package "vnc4server".

---

### Post by diablo75 on 2009-06-09
I installed vnc4server and then ran vncconfig in terminal, but I only get the following as output:

```
No VNC extension on display :0.0

```

Now what?

---

### Post by diablo75 on 2009-06-13
Bump.

---

