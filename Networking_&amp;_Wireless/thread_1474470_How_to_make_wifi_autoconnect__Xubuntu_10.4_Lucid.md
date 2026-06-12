---
title: "How to make wifi autoconnect ? Xubuntu 10.4 Lucid"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by nilou on 2010-05-06
Hi,

I have installed Xubuntu 10.4 (Lucid) on a PC at my uncle's. He is the happy owner of a Netgear wg121 wireless usb-adapter.

I have followed the instructions concerning installation of the ndiswrapper here:
[https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)

The wg is up and running and everything seems to work perfect... except that, when I reeboot and log in, I have to issue the following commands again, to make the network initialize the wep-encrypted connection. If I do not issue these commands, the wifi-part of the Xubuntu network manager (I don't know the exact name of the program) is invisible in the menu or anywhere on the desktop. (It just says no network where the wifi should be appended). But when I issue these commands in a terminal, then the adapter (wg121) opens and connects to the network:

sudo depmod -a
sudo modprobe ndiswrapper

I have tried the command:
sudo ndiswrapper -m
in order to make Xubuntu connect automatically on opening, but no success. When i look through the log it says something about a .conf file, but not which and how, so I'm a bit lost.

I do hope that someone can give me a useful hint or direction.

Kind regards, Mich.

PS. I have posted this some days ago with an other thread name. I think I made a mistake in giving the earlier post a wrong thread title. I have tried to change the title or delete the old post, but it seems not to be an option. So I'm posting this again with a hopefully more informative title.

---

### Post by iponeverything on 2010-05-06
adding the line to your rc.local and rebooting should fix you up.


```
sudo echo sudo modprobe ndiswrapper >> /etc/rc.local
```

---

### Post by nilou on 2010-05-07
Ok, I believe that I have to insert "modprobe ndiswrapper" before the "exit 0" command that I expect to be in /etc/rc.local.
What will happen with the "sudo", is it required? 
I'll give it at try.
Thanks.

---

### Post by iponeverything on 2010-05-07
> **nilou said:**
> Ok, I believe that I have to insert "modprobe ndiswrapper" before the "exit 0" command that I expect to be in /etc/rc.local.
What will happen with the "sudo", is it required? 
I'll give it at try.
Thanks.

yes, good catch.  Above the exit and without the sudo.

---

### Post by kachkeis on 2010-05-09
Hi there,

Try this thread, it's for the WPN111 but i heard that it COULD be  helping for other Netgear adapters. Or  You just use it for inspiration to find a solution.

[http://ubuntuforums.org/showthread.php?t=1477931](http://ubuntuforums.org/showthread.php?t=1477931)

Cheers,
kachkeis :smile:

---

### Post by nilou on 2010-05-11
> **iponeverything said:**
> yes, good catch.  Above the exit and without the sudo.
I did a phonecall to my uncle yesterday, and guided him through insertion of "modprobe ndiswrapper" just before the "exit 0" statement at the end of /etc/rc.local  This was what was needed to do the job. Now the Netgear lights up and connects on startup.

Thanks for Your helping.

Kind regards :),
Mich.

---

