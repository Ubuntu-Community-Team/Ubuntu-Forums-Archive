---
title: "SoundConverter needs python-gstreamer 0.10!"
date: 2009-12-26
forum: Multimedia Software
---

### Post by Depressed Man on 2009-12-26
After doing a Google search for this issue and trying the solutions (which I already had installed, both python-gstreamer 0.10! and the multiverse gstreamer bad plugins) it still gives me this error from the command line.

Any idea how to fix it?

---

### Post by mc4man on 2009-12-26
Maybe put your issue into some context - are you trying to install or run soundconverter?
If trying to install do it from a terminal and post output

(there is no package in ubuntu named  python-gstreamer 0.10 ( it's python-gst0.10

---

### Post by Depressed Man on 2009-12-26
I am trying to run it. I've had it running for a while but it recently broke for some reason. And yes I have python-gst0.10  installed (I just did a search in synaptic for python-gstreamer 0.10 and it reported python-gst0.10 but it was already installed).

---

### Post by mc4man on 2009-12-27
Don't really know but what I would try....
soundconverter is just a python script so I'd remove it completely and install a 'fresh' version ( non-cached

```
sudo apt-get --purge remove soundconverter && sudo apt-get clean && sudo apt-get install soundconverter
```

---

### Post by Depressed Man on 2009-12-27
Nope, it just results in the same error. =(

Even reinstalling all the gstreamer plugins doesn't seem to change anything.

Edit: Hmm a reboot, + a reinstall of python-gst0.10 fixed it. Oh well. =)

---

