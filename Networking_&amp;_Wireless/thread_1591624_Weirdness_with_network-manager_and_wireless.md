---
title: "Weirdness with network-manager and wireless"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by tkarakashian on 2010-10-09
I've installed Ubuntu 10.04 on my laptop recently.  Everything was working fine for a bout a week.  Last Thursday morning before heading out on my day, I did a quick update and then shutdown my machine.  I arrived at a friend's house and could not see any wireless networks.  I futzed with it a few minutes and it looks like the driver's loading.  "lsmod | grep b43" shows the modules loaded.  I thought it might be a problem with network-manager, and I wanted to try wicd out anyway, so I ran "sudo aptitude remove network-manager network-manager-gnome", rebooted and did "sudo aptitude install wicd wicd-gtk".  Rebooted again, and it could see the wireless networks.   Great.  I couldn't enter a password, though.  I later found out that's because if you're putting in a passphrase, apparently you have to put quotes around it.

Never the less, I stopped in a local Starbucks and did some browsing while I relaxed with a coffee.  I had no problems.  Shut down (since it's so new, it starts and shuts down so quickly I don't bother with Suspend or Hibernate), went home booted it...can't see wireless.  I decided I didn't feel like dealing with it, so I left it for the AM.  Reversed the process (uninstalled wicd installed network-manager) and I was back on the network.

I haven't had a single lick of trouble with wired networks.  Plug it in, it finds them just fine.  This morning, same issue, but this time I just uninstalled network-manager, rebooted, reinstalled nm and rebooted again.  And, as you can tell, I'm back on the network.

Anyone have any thoughts?  I can't find anything about this issue.

Thanks!
-T

---

### Post by johnnytm on 2010-10-09
I am having similar problem with my wireless. Doesn't matter where I am when I log on. But I have found that simply rebooting without uninstalling or reinstalling anything allows me to connect to the network. It's just a pain to have to boot twice when I want to connect to the internet. I have been dealing with this for a while now and am still looking for a solution.

---

### Post by tkarakashian on 2010-10-10
I'm thinking you're correct there.  I did some further poking and decided to give [Ceni]("https://launchpad.net/%7Evinux/+archive/vinux-lucid") a try to see if it was just the GUI acting up.  I just booted this morning, and Ceni didn't see the wireless card at all, again despite the fact that the modules were loaded.  I'm going to put some effort into updating the Broadcomm drivers.

---

### Post by tkarakashian on 2010-10-11
Found it!  All along, I've been thinking I've been using the proprietary drivers, but that's not the case!  I installed Ubuntu 10.10 beta on this laptop a few weeks back.  I was playing around with it, and installing various "-desktop" packages (xubuntu-desktop, netbook-desktop, etc) to see how I wanted to interact with this latest incarnation of the OS.  Needless to say, that borked my install a bit, so I decided to move down to 10.04 since I was starting from scratch.  It was only then that my problems started.

Fast forward to tonight when I decided I'd update again to 10.10 now that it's released.  I hadn't had issues with 10.10 before, so perhaps that would correct it.   Nope.  I decided to try just compiling the proprietary drivers and installing manually to see what would happen.  That didn't work out, either, but I did notice something: the docs said the module name was "wl", not b43.  I've been verifying b43 was loaded, not wl. Hmmm...I looked in the Additional Drivers manager and sure enough, it said the driver was installed, but not in use!

I went into /etc/modules and b43 was listed, but not wl.  Curious.  I even have a  /etc/modprobe.d/blacklist-bcm43.conf file that's populated with:

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx

It's odd the module was loaded at all, but as soon as I commented out b43 in /etc/modules and replaced with wl, I'm able to boot repeatedly and see the wireless network!  I don't know why the modules were setup like that, but hopefully it'll work for you, too!

---

