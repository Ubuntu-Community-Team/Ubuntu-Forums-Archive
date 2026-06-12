---
title: "help updated to 10.10"
date: 2010-07-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ihike on 2010-07-17
i was running 10.04 I went to the upgrade in the software manager. followed the steps to upgrade info for 10.10. 
the download went fine
it asked to reboot and now my system is hanging at the kubuntu screen. nothing will work. 
what am i doing wrong and can i uninstall this version.
Help 
[email]2ihike@gmail.com[/email]

---

### Post by philinux on 2010-07-17
Moved to Maverick testing forum.

---

### Post by linuxman94 on 2010-07-17
Keep in mind the 10.10 is still ALPHA so it is not as stable as a beta or final release.  If you want to go back to 10.04, you will have to do a clean install.

---

### Post by meborc on 2010-07-17
you know, without a coma in the title, i really thought that the help inside 10.10 has been updated :)

for the OP: use live cd to get to your system and back all data to cd's or external hd... then do a clean install of 10.04

please do not try alpha soft if you are not capable of mending your own system ;) don't take it personally!

---

### Post by awam66 on 2010-07-17
> **meborc said:**
> you know, without a coma in the title, i really thought that the help inside 10.10 has been updated :)

for the OP: use live cd to get to your system and back all data to cd's or external hd... then do a clean install of 10.04

please do not try alpha soft if you are not capable of mending your own system ;) don't take it personally!

I don't think this is very helpful to the question. I too have problems booting into the present build of Kubnutu. The process stops with a screen full of error messages and nothing happens. I will have to try again to see what the errors are, but only managed to get into Kubuntu, which I am using now by booting to the rescue option and then dropping to a root shell, logging in and manually starting X. Sometimes this works, as now, but other times it fails with file not found errors.
PS I am an experienced user so know what I am doing in general.

---

### Post by ranch hand on 2010-07-17
You really should have a stable version on the drive with your testing version.  That way you can do update(s)/upgrade(s) through a chroot environment.

This is easier than doing them through the recovery options because you can check files and so forth with nautilus on your stable install.

One thing that I would do is run;
```

sudo dpkg --configure -a

```
either in the recovery mode or, preferably in chroot terminal.   Chroot is better as you can copy/paste the terminal generated error messages to this forum and to a gedit file for your own reference.

Other than that I would say that you just need to be patient and upgrade daily.  I would use;
```

sudo apt-get dist-upgrade

```
there is the danger of screwing your system with that command but yours is already screwed, you need all the new stuff you can get.  At least that is my attitude when I have a problem like that.

If you are installed on a / and a /home partition you could reinstall using a daily build and just format the / partiton so that, hopefully, your data makes it through the ordeal (backing up recommended).

---

