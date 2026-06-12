---
title: "GLib version too old (micro mismatch)"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2011-04-09
Still having great fun trying to install 11.04 64 bit on an AMD64 PC (without success). I'm trying to update Maverick 2.6.35-28 to Natty (2.6.38-7 or -8).
I did a clean install of Ubuntu 2.6.35-22 64 bit and updated to 2.6.35-28 without any problems. PC booted fine. 
Installed device drivers for Nvidia G73 Geforce 7600 GS and Broadcomm wireless card. Rebooted and everything fine.
Then I modified my sources.list changing natty for maverick. The sources list was unmodified prior to this and had no additional sources added. Performed a
```
sudo apt-get update
sudo apt-get upgrade
```
and got the following error(s):
```
Processing triggers for libgtk2.0-0 ...
Cannot load module /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: GModule (/usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)
...
/usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so does not export GTK+ IM module API: GModule (/usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)
```
Anyone else had this problem ? 
I can't currently run Ubuntu Natty 2.6.38-7 or 2.6.38-8, but can run Kubuntu Natty without any problems on the same PC. I briefly had Ubuntu Natty running on this machine a few installs back but screwed up the Unity and Compiz settings.

---

### Post by seeker5528 on 2011-04-11
> **Kevbert said:**
> Then I modified my sources.list changing natty for maverick. The sources list was unmodified prior to this and had no additional sources added. Performed a
```
sudo apt-get update
sudo apt-get upgrade
```

Doing 'sudo apt-get upgrade' won't install anything with new or changed dependencies, so either you have to follow it up with 'sudo apt-get dist-upgrade' or use Synaptic or some other frontend to the apt utilities to pick and choose which updates to install.

Typically I would do 'sudo apt-get dist-upgrade' first then review the list of things that would be removed to see if I'm OK with that before continuing.

If I didn't like what dist-upgrade would do, then I would cancel it and fire up Synaptic, manually choosing updates to install, looking for the things that make the least drastic changes first, cancelling the stuff that would make drastic changes and coming back to those packages later.

Also for groups of packes, like vlc and it's related packages, samba and it's related packages, avahi and it's related packes, etc... you may run into where some of the packages will install and other won't, typically I would cancel those, choosing a different one of the related packages to install first because sometimes the order you choose the packages in matters and if I can't find a combination the allow all the related packages to install hold of upgrading any of those packages until later. 

Then I go through Synaptic's list of obsolete or locally installed packags, first removing package that don't cause other packages to be removed, then once I have the list down to a smallish size start revisiting the packages I previously canceled the removal of.

Typically, this late in the game, I would have just used update manager, but it's a little late for you to do that now. :p  There is still potential any time during the development cycle that some interdependent group of packages might not have all landed in the repositories together, which then creates issues when you try to update with update manager, but it's less likely than it is earlier in the development cycle.

Later, Seeker

---

### Post by Kevbert on 2011-04-15
Finally got 11.04 working after installing today's daily build. Thanks seeker5528 for your suggestions it must have been some packages out of sync.

---

