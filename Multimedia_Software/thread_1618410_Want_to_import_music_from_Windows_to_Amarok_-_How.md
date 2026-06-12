---
title: "Want to import music from Windows to Amarok - How?"
date: 2010-11-10
forum: Multimedia Software
---

### Post by erikvduyn on 2010-11-10
So I just set up a dual-boot with Windows 7 and Ubuntu and got myself Amarok. Now, since itunes refuses to work under Wine (and won't uninstall either, some help with that would be appreciated too), Amarok is apparently a good alternative. Problem is, I want to somehow import my itunes library from my Windows into my Amarok library.

Is this possible? If yes, how?

---

### Post by Chronon on 2010-11-10
Just tell Amarok to include the base directory of your itunes library and it should import everything.

---

### Post by erikvduyn on 2010-11-10
> **Chronon said:**
> Just tell Amarok to include the base directory of your itunes library and it should import everything.

That's the problem. When I try to navigate there from Amarok, it says 'could not mount the following device' when I click on the drive with my music on it.
This is using 'play media' btw.

---

### Post by Chronon on 2010-11-10
Mount the volume first.  Then select the directory in

Settings > Configure Amarok > Collection

You might want to set up the partition to automount in fstab.

---

### Post by erikvduyn on 2010-11-10
> **Chronon said:**
> Mount the volume first.  Then select the directory in

Settings > Configure Amarok > Collection

You might want to set up the partition to automount in fstab.

How do I mount that? Does fstab come with Ubuntu? Where do I find it?

You'll have to excuse me, supernewbie at Linux.

---

### Post by Chronon on 2010-11-10
Does the paritition appear in your file browser?  Open it and it should prompt you for your password.  After this it should be accessible.

If you want to automatically mount your Windows partition(s) you need to edit the file /etc/fstab either by following these instructions:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

or installing and using this tool (haven't tried this):
[http://www.hackourlives.com/auto-mount-windows-partitions-in-ubuntu-10-04-lucid/](http://www.hackourlives.com/auto-mount-windows-partitions-in-ubuntu-10-04-lucid/)

Here's another GUI tool:
[http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html](http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html)

---

