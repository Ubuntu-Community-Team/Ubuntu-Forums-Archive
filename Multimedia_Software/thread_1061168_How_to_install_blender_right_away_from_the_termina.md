---
title: "How to install blender right away from the terminal?"
date: 2009-02-05
forum: Multimedia Software
---

### Post by nikgoss on 2009-02-05
Guys,

need help in installing blender (video editing software) right away from the terminal.
Do any of you know how to?? I tried to look in the Synaptics but wasn't there.. what other ways do we have??

plz, help.

---

### Post by gandaran on 2009-02-05
> **nikgoss said:**
> Guys,

need help in installing blender (video editing software) right away from the terminal.
Do any of you know how to?? I tried to look in the Synaptics but wasn't there.. what other ways do we have??

plz, help.
are you sure it isn't in synaptic? what version of ubuntu do you have?
the command for install is
**sudo apt-get install blender**
if it's not in synaptic then you won't be able to install by the command line too.

---

### Post by ohgodnotanother1 on 2009-02-05
Download it from: [http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)
Extract and start from console.:p

---

### Post by ad_267 on 2009-02-05
Edit your /etc/apt/sources.list file and make sure the universe repository is enabled by uncommenting the lines that looks something like:
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid-updates universe

Or you can do this using the gui by going to System - Administration - Software Sources and making sure universe is ticked.

---

