---
title: "Can not forward X11 on remote SSH enabled web server."
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by johnny111 on 2009-09-15
I have recently bought a hosting plan which offers remote SSH. SSH and SSHFS work fine but I am unable to use X11 forwarding, which I would like for running X11 applications on my remote web server.

I established first that the web server had no support for X11:
    ```
./xeyes: error while loading shared libraries: libXmu.so.6: cannot open shared object file: No such file or directory
```
I fixed this by copying my libXmu.so.6 library file to my web server's home directory and running:
    ```
export LD_LIBRARY_PATH=~/
```
It then gave me the message:
    ```
Error: Can't open display:
```
I discovered that the $DISPLAY environment variable is not set, despite me calling SSH with the -X (X11 forwarding over SSH) flag.

How can I set up secure X11 forwarding over SSH?

---

### Post by i.r.id10t on 2009-09-15
ssh -CY username@remotehost

Then login and start a GUI app.

This of course assumes you have a X server on your local machine.

---

### Post by johnny111 on 2009-09-15
> **i.r.id10t said:**
> ssh -CY username@remotehost

Then login and start a GUI app.

This of course assumes you have a X server on your local machine.

This did not solve the problem. Also, -Y is not secure.

---

### Post by i.r.id10t on 2009-09-15
/etc/ssh/sshd_config may be blocking it...

---

### Post by johnny111 on 2009-09-18
I managed to get X11 to work...

I ran an X server without access control then set up a port forward on my router to my local IP address on port 6000 (the default X11 port). I then ran:
    ```
export DISPLAY=<my external IP address>:0.0
```
I was then able to run xeyes.

Although I still have the problem that this is not secure, as well as requiring me to run an exposed X server without access control. Is there a way I can manually forward port 6000 through SSH?

---

