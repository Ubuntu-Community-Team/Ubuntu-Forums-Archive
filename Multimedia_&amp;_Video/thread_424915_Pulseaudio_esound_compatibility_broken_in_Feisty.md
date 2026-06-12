---
title: "Pulseaudio esound compatibility broken in Feisty?"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by erm67 on 2007-04-27
I am trying to set up ubuntu Feisty Fawn release to use pulseaudio whenever is possible but simply replacing esd with pulseadio-esound-compat does not work, I could not hear sounds the logs where filled with messages from gnome apps trying to restart esd as if it were not running and the whole system was unstable.

Using strace I found the reason: the pulseaudio esd compatibility module creates the socket in /tmp/.esd/socket while all application playing to esd expects the socket to be in /tmp/.esd-<uid>/socket in my case is /tmp/.esd-1000/socket.
Am I the only one with this problem?
I currently solved the problem adding this line to /etc/rc.local
ln -s /tmp/.esd /tmp/.esd-1000
but is just a workaround.

---

### Post by zasf on 2007-04-28
I had exactly the same problem, there are some bugs open on pulseaudio but I think we should attract developer's attention to this problem.

---

### Post by erm67 on 2007-04-28
> **zasf said:**
> I had exactly the same problem, there are some bugs open on pulseaudio but I think we should attract developer's attention to this problem.
I opened a bug :confused: 
But now I uninstalled pulseaudio and I am using plain alsa (dmix asym dsnoop) configuration.

---

### Post by zasf on 2007-04-29
I subscribed to [bug #108577]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/108577") and commented.

---

