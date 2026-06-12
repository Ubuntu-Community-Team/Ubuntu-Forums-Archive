---
title: "Quickly close certain ports"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by rfictus on 2012-05-14
I want to quickly block access to (stealth) ports 135, 137, 138, 139. What is one command line that would certainly get the job done?

---

### Post by suspect x on 2012-05-14
hi there,

first you need to know which program is using these ports.
If you want to find out, which exact program is responsible for an open port, type:
```
sudo fuser -v 25/tcp
```
replacing 25 in the example with your desired port. This should tell you which program is running.

From then on, you have several possibilities. First, you can just uninstall the corresponding program, in this case the mailserver that's running. Second, if you want to keep the program, you could try just stopping the service, like so:

```
sudo stop exim4
```

---

