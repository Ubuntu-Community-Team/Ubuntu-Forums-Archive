---
title: "Atheros AR2413 not working after 11.04 upgrade"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by NickUhlig on 2011-06-12
After upgrading to 11.04 about six weeks ago I've had no sufficient solution to my inability to connect to wireless.  Here is a summary of the problem:

After the upgrade, nm is running, and lspci detects my wireless controller (Atheros AR2413 802.11b/g), but nm can only sporadically detect/connect to wireless networks.  Essentially what happens is that upon startup, I have to wait (sometimes 5 minutes, sometimes hours) for the computer to "decide" that it wants to detect the networks, at which point I can connect.  After this it is fine; it doesn't disconnect after this point, but more often than not it takes so long to start working that I might as well not use the computer.

I've tried "Connect to Hidden Wireless Network", to no avail.  I should mention that I also run under the Gnome Classic UI, because Unity is one of the worst UI changes I've ever seen in a version.  I've read that Unity causes some problems with NM, but I have no corroborating evidence of this, and the problem persists even without using the Unity UI.

Any ideas?  Someone recommended using an older kernel, but the file "menu.lst" doesn't even exist in the /boot/grub folder, so I have no idea how I would do that.

---

### Post by ajgreeny on 2011-06-12
I presume from your post that you are  not dual booting and therefore do not see a grub menu at bootup.  If you hold shift at boot time, after the POST has checked everything, a grub menu should appear, and you may be able to boot and get a good connection from whatever kernel you were using in your previous ubuntu version.

There has been no **menu.lst** file for the past 3 or 4 ubuntu versions, since grub2 became the default.  It is now replaced by **grub.cfg**, but there are greater differences than just that file, which itself is read-only and can not be edited direct, so read and ingest the info on grub2 linked to in my signature for all the details.

---

### Post by NickUhlig on 2011-06-14
Well, that seems to have solved the problem.  I guess I'll take it for now, but I would have hoped that I could get a solution for these wireless problems that would still allow me to use the new kernel.

Thanks!

---

### Post by lalitchandnani on 2012-06-23
You can still work on new kernel with working Wireless connection using following steps.
1. Switch to Ubuntu "Classic" desktop view : For that you can find the instructions here:
    [http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/](http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/)

2. Install wicd package using any of package manager.
    e.g. **sudo apt-get install wicd.**

3. Change back desktop view to "Unity" using same flow as mentioned in 1.

Wireless connection should work for you.

---

### Post by coffeecat on 2012-06-23
Old thread closed.

---

