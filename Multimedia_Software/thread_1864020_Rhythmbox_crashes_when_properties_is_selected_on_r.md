---
title: "Rhythmbox crashes when properties is selected on removable media menu"
date: 2011-10-18
forum: Multimedia Software
---

### Post by splinter701 on 2011-10-18
Hi guys
I just recently upgraded from 11.01 to Ubuntu 11.10, and with it came this bug.
When I load my iPod nano 5g or any other removable media player device (I tried a few) into rhythmbox and go to 'properties on the menu, the program just crashes.

'segmentation fault' is the only seemingly useful thing printed to the terminal when this happens, though if necessary I will post a full log. There have been a few bug reports on this subject on launchpad as well though.

I'd really appreciate it if anyone could tell me why this is happening and how I can fix it.

---

### Post by splinter701 on 2011-10-19
If this thread is in the wrong section feel free to move it. Does anyone know anything about this issue? I can reproduce the bug anytime.

---

### Post by splinter701 on 2011-10-20
bump

---

### Post by splinter701 on 2011-10-20
another bump, does anyone actually read these?

I just tried 

```
sudo apt-get purge rhythmbox
sudo apt-get autoremove
sudo apt-get install rhythmbox
rhythmbox
```and then tried to select properties on my ipod

and still get the segmentation fault in the command line output. Does anyone know whats going on here?

---

### Post by splinter701 on 2011-10-21
I'm just gonna bump this a couple of times a day till someone replies...

---

### Post by splinter701 on 2011-10-21
posted the same thread in another section. Hopefully i get more replies there....

---

