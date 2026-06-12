---
title: "Broadcom 4318 Wireless Issue"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by svtguy88 on 2011-09-08
I'm trying to get my wireless card working properly.  lspci reports that my card is a BCM4 4318.  I've got b43/fwcutter installed, and the interface shows up as wlan0.  I can also see networks when I click on the network manager applet.  However, I am unable to connect.  When I click on a network, nothing happens.  The same nothing happens when I try to create a network.

I am also connected via ethernet, but the same problem occurs if I disconnect from the wired network.  Ideally, I'd like to be connected to both the wired network and wireless (actually, I want to be connected to ethernet, and host an ad-hoc wireless to act as a WAP for my house).

Any help would be appreciated.  There's not much holding my Powermac to OS X any more, other than proper wireless and 3d-acceleration...

---

### Post by fdrake on 2011-09-08
> **pkmgarf said:**
> I'm trying to get my wireless card working properly.  lspci reports that my card is a BCM4 4318.  I've got b43/fwcutter installed, and the interface shows up as wlan0.  I can also see networks when I click on the network manager applet.  However, I am unable to connect.  When I click on a network, nothing happens.  The same nothing happens when I try to create a network.

I am also connected via ethernet, but the same problem occurs if I disconnect from the wired network.  Ideally, I'd like to be connected to both the wired network and wireless (actually, I want to be connected to ethernet, and host an ad-hoc wireless to act as a WAP for my house).

Any help would be appreciated.  There's not much holding my Powermac to OS X any more, other than proper wireless and 3d-acceleration...

can you post the results for:

```
dmesg | grep wlan0 
iwconfig
sudo lshw -c Network
nm-tool
lsmod
less /etc/modprobe.d/blacklist | grep -e bcm -e b43

```

is your essid encrypted? have you tried to connect to an open network?

---

### Post by svtguy88 on 2011-09-09
I'll try to post the output of those commands tonight still.  I'm stuck back in OS X world for the time being though, as the roommates demanded I get wifi back up for the night.  If I don't boot back to linux before I go to bed, I'll post everything in the morning.

And no, I have not tried connecting to a non secured network yet, just tried clicking on all of the visible ones (all of which are secured).

---

### Post by svtguy88 on 2011-09-09
Strange.  I was fiddling with some X server issues (trying to get nouveau to behave), and broke a bunch of packages.  I spent a long while in aptitude, and got my X server back.  Now I can connect to wireless...maybe it just needed a reboot?  I don't recall if I rebooted after installing fwcutter...

---

### Post by fdrake on 2011-09-09
> **pkmgarf said:**
> Strange.  I was fiddling with some X server issues (trying to get nouveau to behave), and broke a bunch of packages.  I spent a long while in aptitude, and got my X server back.  Now I can connect to wireless...maybe it just needed a reboot?  I don't recall if I rebooted after installing fwcutter...

aptitude?  probably you just run few updates that fixed your issue. sometime updates/upgrades are the first solution to try. 

glad to hear that! :D

---

### Post by svtguy88 on 2011-09-09
That's the funny thing, is I was keeping a pretty close eye on what was getting updated, and it was pretty much only X11 stuff.

Whatever.  I have X back, and wireless seems to work now too.  

My next issue is that my created (ad-hoc) wireless network is not visible from other machines.  The network manager applet shows me connected to it, but my laptop does not see it.  I also tried "connect to hidden network" and just typed in the name I provided, but still nothing...

---

