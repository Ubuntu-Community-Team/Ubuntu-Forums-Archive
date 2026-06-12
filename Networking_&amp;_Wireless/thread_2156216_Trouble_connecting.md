---
title: "Trouble connecting"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by aviatorknight on 2013-06-20
> **Ditchdoc7893 said:**
> I actually got it working, however it was not using any of the above methods. Here's how:

In Synaptic:
-uninstall bcmwl-kernel-source completely
-install firmware-b43-installer and b43-fwcutter 
 
In terminal:
```

cat /etc/modprobe.d/* | egrep 'bcm'

```

See if 'blacklist bcm43xx' shows up. If it does, type in terminal:

```

cd /etc/modprobe.d/

```
then...
```

sudo gedit blacklist.conf

```

Find the line "blacklist bcm43xx" and comment it out by placing a # in front of it.
Save the file.
Reboot the system.
I'm having similar problems, but... Well... They're a little more complicated as I have much less experience with linux. 
I'm using the same device under the same conditions, but I'm using 13.4 instead of 12. The thing is, in order to fully attempt or complete the above solution, I need syncopate. It's...
not something the laptop seems to have.
What's worse is:
I could not manage to obtain an ethernet connection whatsoever.
I can't seem to re-do my installation, as it was done via disk.
I can't obtain any charge from my charger, however it seems more than willing to allow itself to run as if it ran off of outlet power from the get go.
(No longer travel friendly)
Please,
Pleasepleasepleasepleaseplease,
Help me re-establish connection to the internet with this machine!

At my disposal is a 2 gb sd card,
a seemingly useless burned installation disk labeled "Ubuntu 13 32-bit" in sharpe,
and an ARM samsung chromebook.

---

### Post by Bucky Ball on 2013-06-20
***Post moved to own thread. ***

Please do not hijack threads. Your problem is NOT the same. Hijacking threads causes confusion, dilutes community effort, is unfair to the OP and reduces your chances of getting help (as the thread title doesn't match your problem specifically and you are buried 10+ posts deep).

Change the thread title of this thread to something more appropriate (let me know and suggest something if you can't change it) and add more info about your problem. Good luck.

---

### Post by wildmanne39 on 2013-06-21
Thread closed. Please do not post duplicates, it dilutes community effort.

---

