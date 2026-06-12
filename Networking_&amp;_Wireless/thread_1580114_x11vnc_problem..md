---
title: "x11vnc problem."
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by andres.ordonez on 2010-09-22
Hi, I want to access my desktop from my laptop over the internet, after a while I found this

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

so I followed the instructions "Access your PC over the internet" and "Logging in from another Ubuntu PC". Everything goes well until I try to run the shell script and get this:

laptopuser@123.456.7.890's password:

Is this supossed to happen?
anyway, I tried my luck with the passphrase associated with the rsa key, with the password of the laptopuser@laptop and with the password of the desktopuser@desktop but I keep getting Permission Denied (publickey, password).

Thanks in advance!

---

### Post by perspectoff on 2010-09-22
You must have followed the instructions for storing a password for VNC, since the shell script instructions include that.

The password is then stored in

~/.vnc/x11vnc.pass

where ~ stands for /home/laptopuser in your case.

You don't have to use X11VNC with a password, if you don't want to.

Just leave out the

 -rfbauth ~/.vnc/x11vnc.pass

 option in the script if you don't want to use a password.

Since I always use VNC through a secure SSH tunnel, I don't use a password, for example.

My X11VNC quick instructions are at:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#X11VNC_Server](http://ubuntuguide.org/wiki/Ubuntu:Lucid#X11VNC_Server)

or

[http://kubuntuguide.org/Lucid#X11VNC_Server](http://kubuntuguide.org/Lucid#X11VNC_Server)

---

### Post by andres.ordonez on 2010-09-22
well, so far I haven't come across instructions about storing a VNC password, but I'll see what I can find. Thanks!

---

### Post by andres.ordonez on 2010-09-22
> You don't have to use X11VNC with a password, if you don't want to.

Just leave out the

-rfbauth ~/.vnc/x11vnc.pass

option in the script if you don't want to use a password.

but that option doesn't appear in the script I'm using:

```
#!/bin/sh

ssh -f -L 5900:localhost:5900 123.456.7.890\
        x11vnc -safer -localhost -nopw -once -display :0 \
        && sleep 5 \
        && vncviewer localhost:0
```

---

### Post by krunge on 2010-09-23
Your ssh is asking for a password, right?

---

### Post by andres.ordonez on 2010-09-23
> **krunge said:**
> Your ssh is asking for a password, right?
I'm new to remote networking so excuse me if I don't understand exactly what you are asking me :-k

The first time I did

ssh desktopuser@123.456.7.890

from the laptop, it asked me for the passphrase(rsa), but that was only the first time, now I get connected without providing the passphrase. Was that the question?:???:

---

