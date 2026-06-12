---
title: "Natty hangs at boot"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Squall5668 on 2011-03-31
First of all, im not sure if im supposed to be asking for help about Natty, since its
a development release. Still i broke it myself so its not a Natty problem, could have
happened in 10.10 too :P
Please note: im new to Ubuntu

Ill try to make this as short as i can:

I (for whatever stupid reason) decided to delete Halt & Reboot scripts a while ago, keeping
backups, but seeing that the system was still stable during boot up and shutdown, i deleted
the backups as well

Problem starts at initscripts update in Natty. It simply would not finish installing, so i  rebooted

Natty being in a Virtual-box, it simply crashed every time at boot, be it normal, or repair mode. I decided to chroot from a live CD and restore the 2 deleted files (note:i also felt like an idiot) and run an upgrade to be sure everything was optimal

After all that, it wouldn't crash, but even with splash and quiet deleted i only get errors
at repair mode, normal boot just seems to hang while starting apparmor profiles

In repair mode i get the attached picture (too big to type it, cant copy paste)

Searching for similar problems, i also found people saying i should chown & chmod /etc/*
to root. Tried, but it didn't seem to work either

I could use any help at all. Yes, i could reinstall but its a virtual PC, where is the fun and knowledge in that? :D

ps:yes, i know the firewall isn't configured

---

### Post by Squall5668 on 2011-04-01
Not sure if i'm allowed to bump.
Still haven't found anything searching around, any ideas at all would be helpful
even keywords for searching more efficiently

---

### Post by lisati on 2011-04-02
*Thread moved to **Natty Narwhal Testing and Discussion**.*

---

### Post by cariboo on 2011-04-02
I don't suppose you took a snapshot before you started changing things?

---

### Post by Squall5668 on 2011-04-02
I wish.
Tried fscking from livecd also, as was stated in other similar error.
Did nothing

Any ideas at all? Even getting one more error could be helpful :)

---

### Post by Squall5668 on 2011-04-04
Last bump i guess,
can someone at least tell what causes a drive to become read-only?
From what i found its usually if the drive is corrupt?
Any other common reasons?

---

### Post by Squall5668 on 2011-04-19
I managed to fix this by purging runit (chroot w/ live cd)
Then, I managed to boot in recovery, drop to a root shell with networking 
and reinstall runit (and run an upgrade to make sure)

---

