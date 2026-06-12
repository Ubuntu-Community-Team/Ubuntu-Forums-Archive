---
title: "Can't burn cdrw"
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by tundra2006 on 2007-12-19
I have 7.10 with cdrw.  I have used serptine, k3b, gnomebaker.  and the basic problem is it can't find or mount the cdrw drive.  fairly new to this  can anyone help

---

### Post by timseal on 2007-12-19
In k3b, did you do settings->configure k3b and look at Devices. There's a place to add your drive in there.  
doing a 'cdrecord -scanbus' from a terminal will tell you if the system knows about the drive.

---

### Post by tundra2006 on 2007-12-19
Re: Can't burn cdrw
In k3b, did you do settings->configure k3b and look at Devices. There's a place to add your drive in there.
doing a 'cdrecord -scanbus' from a terminal will tell you if the system knows about the drive.
___________

yes i looked in k3b and it lists my cdrw drive.  i confirmed the same info with the cdrecord-scanbus.

---

### Post by timseal on 2007-12-19
so what is the error message given wodim (that's the program that actually does the writing,invoked by whatever frontend).  I think k3b shows a log after it fails.

---

