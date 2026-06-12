---
title: "Mplayer error after install"
date: 2008-05-02
forum: Mythbuntu
---

### Post by whein on 2008-05-02
Installed from the 8.04 ISO image for i386 and Mplayer works, but before playing a file it throws up the following error EVERY TIME
```
AO:[pulse] Failed to connect to server: Connection refused
```
As I said, everything else I've done seems to work ok with Mplayer, but the error message is annoying.  I've figured out that it has something to do with the pulse audio server (whatever that is) but beyond that I'm stumped.  What does it mean and how do I fix it?
-Will

---

### Post by superm1 on 2008-05-02
Go into /etc/mplayer/mplayer.conf

Change ao=pulse,alsa, to ao=alsa,

---

### Post by casperlingus on 2008-06-03
That is exactly what I have been looking for the past hour.  Thanks!

---

### Post by FrostBlue on 2008-09-07
Hi,
I am getting the error even after the change sugeested and I don't have sound at all in any media player and in games like Nexuiz.Amarok works fine though.

Any clue how to fix this.

Cheers.

---

### Post by FrostBlue on 2008-09-07
Solved it,I selected alsa in mplayer options from the player window.

---

### Post by Egi_Power on 2008-09-07
Hi all!

Had the same problem with mplayer.

> **superm1 said:**
> Go into /etc/mplayer/mplayer.conf

Change ao=pulse,alsa, to ao=alsa,

Tried to edit /etc/mplayer/mplayer.conf simply from nautilus, but couldn't save it.
Had to use:
```
sudo gedit /etc/mplayer/mplayer.conf
```
(You probably know this, but i'm new to Ubuntu and linux.)

Anyway, didn't solve it for me.

> **FrostBlue said:**
> Solved it,I selected alsa in mplayer options from the player window.

Followed your instructions and it did the trick.
mplayer -> preferences -> audio tab -> choose alsa from available drivers.
restart mplayer

Thank you all for the advice.

---

