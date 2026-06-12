---
title: "Alsa stopped working after install of VirtualBox (and after uninstall)"
date: 2008-07-02
forum: Multimedia Software
---

### Post by T4_ on 2008-07-02
I installed VirtualBox, audio kept working. I then shut down for the night (planning to test VB the next day, i.e. now) and my audio does not work anymore.

I've tried reloading and reinstalling Alsa, when that didn't work I removed virtualbox and virtualbox-ose-modules-rt - didn't help. I then tried to reload and reinstall Alsa again, rebooted etc, but nothing - I still can't get audio.

When I try to reload Alsa, it says:
```
koen@pavor:~$ sudo alsa reload
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
```
I've never had to reload Alsa before so I don't know how bad this is (but I'm guessing it's not good).

The same message as above appears after I try reloading Alsa after I've reinstalled it.

When I try to open gnome-volume-control, I get an error message saying that gstreamer plugins/devices are (suddenly) not installed. Currently installing the list of "essentials" in the sticky topic at the top of this forum, as manually reinstalling gstreamer didn't solve the problem.
[edit] After (re)installing the plugins/libs/etc (everything, basically) in that list, it has made no difference. I am lost.

This is on Ubuntu Studio if that helps.

Any ideas will be much appreciated!


[solved}
I decided to do a complete system-wide upgrade just to see what would happen. Upgrade, reboot, and it's working again.

Still a mystery to me, but at least it's working now.

---

### Post by rarsa on 2008-11-11
Somehow installing the Virtualbox-ose-modules corrupts the kernel or kernel modules.

This post [http://ubuntuforums.org/showthread.php?t=830216&page=2](http://ubuntuforums.org/showthread.php?t=830216&page=2) explains that using the previous kernel is the solution.

In my case it was the only way to get my sound back.

But I didn't just removed the entry from the menu.lst, I actually uninstalled the corrupted kernel.

```
sudo apt-get remove linux-image-2.6.24-21-generic
```

Of course your kernel version may be different. You can find it with 

```
uname -a
```

---

