---
title: "KNetAttach Problems"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by BrantlyMedders on 2011-07-20
Greetings all,

I am having a rather odd issue with KNetAttach and trying to access one of my local machines through ssh.

In short, adding the machine through KNetAttach gives me the following error:
```
Unable to connect to server.  Please check your settings and try again.
```  However, good ole sshfs and ssh itself work fine from the command line, and I am able to access the machine normally.  It might be worth noting that I've tried inputting both an IP and the hostname I've configured in /etc/hosts.  Furthermore, it might be worth noting that the Nautilus client works flawlessly.

Can anyone help me solve this?

---

### Post by BrantlyMedders on 2011-07-20
Apparently it was something dealing with .ssh/known_hosts.  I got rid of all entries relating to the machine in question and everything works like a charm now.

---

