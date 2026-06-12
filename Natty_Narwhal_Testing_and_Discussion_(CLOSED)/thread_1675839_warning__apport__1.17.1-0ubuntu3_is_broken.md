---
title: "warning:  apport  1.17.1-0ubuntu3 is broken"
date: 2011-01-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-01-26
some updates about apport today, and this latest is broken

bug report [lpbug]707971[/lpbug]

---

### Post by grubdude on 2011-01-26
Has anyone else had this problem during one of the last couple of updates? If so is there any immediate fix?
 
 
E: apport: subprocess installed post-installation script returned error exit status 1
E: apport-gtk: dependency problems - leaving unconfigured
 
**From Terminal:**
 
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up apport (1.17.1-0ubuntu3) ...
start: Job is already running: apport
invoke-rc.d: initscript apport, action "start" failed.
dpkg: error processing apport (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 apport
 apport-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
Thanks....

---

### Post by tjeremiah on 2011-01-26
yes, I have the same problem and no, I dont know if there will be an immediate fix.

---

### Post by grubdude on 2011-01-26
Thanks. Also, thank you for moving this to the proper thread. :-)

---

### Post by kyleabaker on 2011-01-26
I've got the same problem with the exit status 1 error, except I'm trying to fix mine in recovery mode since I'm unable to boot with the latest updates (as of yesterday's updates). :/

---

### Post by marijus on 2011-01-26
you can fix it by typing this in terminal:

sudo service apport stop
sudo dpkg --configure -a

hope it'll help...
best, marijus

---

### Post by kyleabaker on 2011-01-26
> **marijus said:**
> sudo service apport stop
sudo dpkg --configure -a

Thanks, that fixed the apport issue. Now I've just got to wait out the [xorg updates]("http://ubuntuforums.org/showthread.php?t=1675614") and hope my nvidia card works again soon.

---

