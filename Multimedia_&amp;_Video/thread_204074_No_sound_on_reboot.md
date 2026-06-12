---
title: "No sound on reboot"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by handle1790 on 2006-06-26
Hi all, first post.  I'm pretty new to Linux, and this is my first real problem with it.

My relevant system specs are: Dell e1505 laptop, Sigmatel 92xx audio card, on the latest 686 kernel with smp support.  Its worked for about a month with no issues.

Last night, I shut down the computer, loaded it back up about an hour later, I DID get the "doot doot" sound at the login screen, but no sounds after logging in.  I'm currently running a dual boot, and sound works fine in windows.

When I go to sound preferences, there is no Default Sound Card.  When I go into device manager, it seems to recognize both the card and drivers.

Trying to run alsamixer gives me: alsamixer: function snd_ctl_open failed for default: No such device

I tried reinstalling alsa-base.  This did not help.

I did chmod 777 on both /dev/audio.

I read a lot on modprobes, but without knowing the specifics of what they're actually doing, I didn't want to run something that was a complete hit or miss.

Any help would be appreciated.  Please post if you need more information, as like I said, I'm a linux newbie.  Thanks much in advance. 

-Dan

---

### Post by handle1790 on 2006-06-26
Fixed!

The problem was in the user permissions.

I realized I was overcomplicating it, since I was getting the first sound at the login screen, so I looked up permissions instead of driver information, and that was it :D

Feel free to lock this post!

---

