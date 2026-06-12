---
title: "Mythbuntu: how to start a VNC server at login?"
date: 2012-12-20
forum: Mythbuntu
---

### Post by Erik-NA on 2012-12-20
In mythbuntu 12.04, how do I start a (x11VNC) VNC-server at the log in prompt?

If I ssh to the machine I can run:```
sudo x11vnc &#8211;display :0 &#8211;auth /var/lib/lightdm/.Xauthority
``` to manually start the VNC-server, but how do I do it automatically in Mythbuntu 12.04 using a session password?

---

### Post by dannyboy79 on 2012-12-20
possible solution here, post #2
[http://ubuntuforums.org/showthread.php?p=12226623](http://ubuntuforums.org/showthread.php?p=12226623)

---

### Post by nickrout on 2012-12-20
> **Erik-NA said:**
> In mythbuntu 12.04, how do I start a (x11VNC) VNC-server at the log in prompt?

If I ssh to the machine I can run:```
sudo x11vnc –display :0 –auth /var/lib/lightdm/.Xauthority
``` to manually start the VNC-server, but how do I do it automatically in Mythbuntu 12.04 using a session password?
Mythbuntu-control-center - services tab

---

### Post by Erik-NA on 2012-12-20
> **nickrout said:**
> Mythbuntu-control-center - services tab

Nope. That setting is only installing x11vnc server. You have to manually start x11vnc after logging in.

---

### Post by steeldriver on 2012-12-20
is this the info you are looking for?

[http://ubuntuforums.org/showthread.php?t=2090922&highlight=session.sh](http://ubuntuforums.org/showthread.php?t=2090922&highlight=session.sh)

---

### Post by Erik-NA on 2012-12-21
> **dannyboy79 said:**
> possible solution here, post #2
[http://ubuntuforums.org/showthread.php?p=12226623](http://ubuntuforums.org/showthread.php?p=12226623)

This worked flawlessly, thanks!

---

