---
title: "Can only ssh TO my machine if I am logged in at console"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by mcfiddish on 2009-05-09
I did a clean install of 9.04 last night and restored my home directory from backup.  Now I can only ssh to my machine from another on my home network if I am logged in at the console.  If I am not logged in at the console, the ssh connection times out.

I have tried to ssh when I am not logged in, then while the remote session is waiting (for what?) I log into the console and then the remote connection completes normally.

I noticed that ssh-agent runs when GNOME starts up ont the console.  Does this have anything to do with it?

---

### Post by mcfiddish on 2009-05-09
Also, if I am logged in at the console, and ssh from a remote machine, then log out of the console, the remote session freezes.  If I log back into the console, the remote ssh session resumes.

---

### Post by mcfiddish on 2009-05-09
Previously I used to enter my network information manually in the /etc/network/interfaces.  This time I tried the GNOME administration tool from the menu.  Evidently it brings the network up and down just when you're at the console.  I removed those settings and edited  /etc/network/interfaces like I used to, and now it all works again.

---

