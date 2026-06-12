---
title: "mount samba share"
date: 2012-07-16
forum: Networking &amp; Wireless
---

### Post by DrScum on 2012-07-16
I'd like to mount a samba share on an ubuntu 12.04 desktop on my laptop (running 10.04) in order to synchronize with grsync. 

I can access the desktop share through the file manager, but when I try to mount it the error message is: mount error (6): no such devcice or adress

Any Ideas out there? Some help would be greatly appreciated.

---

### Post by DrScum on 2012-07-16
after two hours trying and searching I found a solution:

on the ubuntu 12.04 server the packages
samba
system-config-samba
samba-doc

were installed, the share was configured and a samba password was created.

On the laptop Ubuntu 10.04 LTS is running, the package
samba
is installed

the mount point <mountpoint> was created

At this point the following console command successfully mounts the share:

sudo mount -t cifs -o username=<username>,password=<password> //192.168.0.174/<share name> /<mountpoint

apparently <share name> can only have the sharename and NOT the path. If you enter the path to the share here you get an error. That's what put me off for so long.

---

### Post by OM55 on 2012-07-16
So please mark this thread as 'Solved'...

---

### Post by DrScum on 2012-07-16
I thought I did. I added "[solved]" to the title. Is there another way that I don't know?

---

