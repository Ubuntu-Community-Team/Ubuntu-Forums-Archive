---
title: "Error while trying to install multimedia codecs"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by ArnsteinK on 2007-03-10
I get this message:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by RomeReactor on 2007-03-10
Hi. If you're using Ubuntu (not Kubuntu) make sure "Add-Remove" or "Update Manager" (the orange square in the top panel, next to the little speaker) are not running. also, are you trying to install from the Terminal? Remeber you **must** prepend **sudo** to apt-get to install software:

```
**sudo** apt-get install PACKAGE_NAME
```

---

### Post by ArnsteinK on 2007-03-11
I managed to do it now. All I had to do was to close synaptic. But the sound still don't work. I read on a forum that I had to install isapnptools and I did. How do I use it? I don't  know how to open it :P

---

### Post by RomeReactor on 2007-03-12
What packages did you install? And what sound card do you have (integrated or other)?

---

