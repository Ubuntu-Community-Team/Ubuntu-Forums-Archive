---
title: "qtparted problem"
date: 2008-06-19
forum: Mandriva/Mageia
---

### Post by logos34 on 2008-06-19
The gui launches but I get an error message about it not detecting any drives. (fdisk sees the drives fine).  Anyone know of any bugs/issues I should be aware of?

---

### Post by pelle.k on 2008-06-19
qtparted is more or less unmaintained software by now, 0.4.5 being released in 2005. gparted is highly recommended.
I cant help you with your problem though. Sorry.

---

### Post by logos34 on 2008-06-19
ok, thanks, just wondering.  I'd use gparted but I'm on the default KDE desktop, so prefer a qt-based gui.  Maybe I'll try Kparted

(edit: guess I won't--kparted can't edit and it's ancient to boot)

DiskDrake will have to do...

---

### Post by Shazaam on 2008-07-02
Mandriva is a great distro but I had a problem with Mandi 2007. Before it was installed I ran it as a livecd and qtparted showed both drives as unpartitioned space when in fact they had PuppyLinux, Ubuntu and WinXP on them. 2008 did the same thing.
Since then I have gotten into the habit of using the gparted livecd to set up partitions first and then point the installers to said partitions. Yes, a little more effort but it works for me.

---

