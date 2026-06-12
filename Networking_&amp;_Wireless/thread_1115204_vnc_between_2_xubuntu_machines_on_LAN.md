---
title: "vnc between 2 xubuntu machines on LAN"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by pickarooney on 2009-04-03
I've installed vnc4server and gtkvncviewer on both by machines but when I try to connect from one to the other I get 'you have been disconnected' each time. The server is running on boht machine bu tI'm logged into each as a different user. I had  to set up a password when running the server. To connect, should I use the remote or local user and password? I've tried all 4 combinations already but with no luck.

What else might be preventing me connecting? I don't have any firewall software and the machines can connect via SSH.

---

### Post by pickarooney on 2009-04-04
I can't connect to each machine from itself either, which is a little strange.

---

### Post by pickarooney on 2009-04-05
I managed to connect one of the machines to itself via VNC on port 5901 but I only got a basic xterm interface and nothing else, plus I can't connect from the other machine.

I've tried finding tutorials on this but they all seem to hinge on the connections coming from the outside.

---

### Post by pickarooney on 2009-04-12
I switched to tightvnc and made a little progress, but not much.

I ran **vncserver :64 -geometry 1024x768 -depth 16 -name marklar**
Then I ran **vncviewer -via 192.168.1.10 localhost:64** from the desktop, to see could I connect to myself, but only a grey cross-cross screen opened up.

If anyone is reading... what can I do now?

---

### Post by pickarooney on 2009-04-13
Solved this by installing the KDE network package which included krdc and krfb

---

