---
title: "having problem with x11vnc ..."
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by zopanp on 2009-05-18
hello evryone,
I'm having a problem using x11vnc on a ssh connection, eventough my ssh connection is working when I run x11vnc he ony allow me to display my desktop ...
here are the command I runned :
```

ssh username@domain.name
password : **********

```
then in an other shell :
```

x11vnc -forever -shared -display :0

```
and the only display i have is my desktop ....

Please help.

Thanks

---

### Post by krunge on 2009-05-18
> **zopanp said:**
> 
and the only display i have is my desktop ....


It's not clear to me what you are trying to do.  There need to be two desktops: 1) the one x11vnc exports via VNC and 2) the one where you are sitting where the VNC viewer is run.

Do you actually want to do X11 application forwarding via ssh instead? (I.e. no VNC)

---

### Post by zopanp on 2009-05-18
I want to see the desktop of my computer2 from my computer1 but the only desktop I get is my computer1.
I already have a ssh connection and I am trying to use X11vnc with ssh.

thanks

---

### Post by krunge on 2009-05-18
> **zopanp said:**
> I want to see the desktop of my computer2 from my computer1 but the only desktop I get is my computer1.
I already have a ssh connection and I am trying to use X11vnc with ssh.


```

computer1> ssh -L 5900:localhost:5900 user@computer2
Enter password, etc..

Then in that computer2 shell run x11vnc:

computer2> x11vnc -localhost -display :0 -rfbport 5900

Then in a 2nd terminal on computer1:

computer1> vncviewer localhost:0
```

More info here: [http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling) (and also in these forums.)

---

### Post by zopanp on 2009-05-21
do I have to install x11vnc on the the computer2 ?
thanks.

---

### Post by krunge on 2009-05-21
> **zopanp said:**
> do I have to install x11vnc on the the computer2 ?

Yes.  And there is no need to install x11vnc on computer1.

---

### Post by zopanp on 2009-05-22
thanks I now understand why it wasn't working, i was running x11vnc from computer 1. isn't it possible to run x11vnc on computer2(trough ssh) from computer1, because computer2 is an old mac with no memory left ?

thanks for your fast reply

---

### Post by krunge on 2009-05-22
> **zopanp said:**
> thanks I now understand why it wasn't working, i was running x11vnc from computer 1.
Yes.  Glad it is working now.
> isn't it possible to run x11vnc on computer2(trough ssh) from computer1, because computer2 is an old mac with no memory left ?


Below I assume you are running Unix/Linux on the old mac and not Mac OS X (x11vnc works natively on Mac OS X, but I assume you are not doing that.)

This can be done:  [http://www.karlrunge.com/x11vnc/faq.html#faq-noshm](http://www.karlrunge.com/x11vnc/faq.html#faq-noshm)

Think of your old mac as the machine referred to as "Xterminal" in that FAQ.

But note that it can be very slow this way or otherwise hog your network.  This is because x11vnc will be polling and reading computer2's framebuffer over the network instead of over the local hardware. There is no compression, it is all raw copies. This can easily saturate 100Mb/sec ethernet even when nothing is changing on the screen. If computer2 is extremely slow I guess this mode could actually help...

---

