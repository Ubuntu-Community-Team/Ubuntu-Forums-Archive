---
title: "Computer naming"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by Deep fried ice-cream on 2009-01-27
Firstly, good work to the Ubuntu dev team, I had a extensive configuration and compiling plan to get Wireless networking going, none of which was needed. [http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

Any way, I'm a bit of a newbie, and running a fresh install of Ubuntu 8.10 on my new Laptop, but I put in an incorrect name for my computer during the install, and I'd really like to know how to change it. Also While terminal commands would almost certainly work, is there a GUI solution to this, and if so, could you please explain it along with the terminal commands (learning how to do this both ways is more important to me than getting this done, I COULD just re-install the OS.)

---

### Post by bgerlich on 2009-01-27
Making changes to linux config is dead simple and intuitive. All global config files are stored in the /etc dir, all per-user config files are in the home directory (as hidden dirs, meaning starting with a dot).

All you have to do is edit in any way you like the file /etc/hostname . Remember that the file can only be edited by root so you'll have to start the editor or file browser with sudo or gksu giving the started program administrative privileges.

---

### Post by Deep fried ice-cream on 2009-01-27
Damn, I'm Impressed...
pity it doesn't mention that anywhere,
anyway, thanks

---

### Post by Iowan on 2009-01-27
One possible caveat - change /etc/hosts file, too. Details [here]("https://bugs.launchpad.net/ubuntu/+source/hostname/+bug/113778").

---

