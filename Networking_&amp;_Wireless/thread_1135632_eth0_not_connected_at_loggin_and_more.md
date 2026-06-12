---
title: "eth0 not connected at loggin and more"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by pewp on 2009-04-24
Because I'm still GUI dependent on a few things I've been running Ubuntu desktop edition to serve ftp, http, and some gaming oriented servers.  I was having an issue where I would have no network connectivity unless a user was logged in which made it a pain when I needed to restart the machine remotely (I wouldn't be able to ssh back in).  So, I added a line to the interfaces file which was:

auto eth0
iface eth0 inet static
address
subnetmask
gateway

interfaces only had auto lo before that.  That seemed to do the trick in terms of allowing me to have connectivity prior to logging into an account.  Once I got to the machine and physically logged in I was met with an error with the eth0 interface.  So, I removed the line, rebooted, and all was fine again.

So, my question is how can I have my cake and eat it too?  What am I doing wrong that will not allow me to have connectivity both before and after a user login?  I realize that for running servers I need to just go server edition and scrap the GUI, but I don't feel I'm ready for that plunge yet.

Also, I've been having horrible transfer speeds with proftpd.  I checked the conf and reversedns and ident lookups are set to off, which is what I have read as the most frequent reasons for slower connection speeds.  I've tried both passive and active modes and it's the same either way.  Anyway to diagnose this issue?  I don't have any slowness with any of the other servers I'm running, and I'm not maxing my connection out with what I'm doing outside of FTP.  It's 6Mbps up/down and transfer speeds suck regardless of what is running along side it.

I'm in the proccess of downloading the packages for the 9.04 upgrade.  I'm hoping that might solve some of my issues.  If anyone has any information to assist me, I would appreciate it very much.

---

### Post by pewp on 2009-04-27
Just a bump to this.  I upgraded to 9.04 and it seemed to fix my ftp slowness, not sure where the problem was there.   

On the topic of the eth0 thing.  It seems that if network manager is installed and you edit /etc/network/interfaces to contain an entry for an interface that network manager uses it gets all screwy.  I uninstalled network manager and installed wicd and the eth0 interface starts up at boot so I can now reboot my machine remotely and get back in without having to login as a user, which is all i wanted.  I know i could have just uninstalled network manager and kept the iface eth0 auto eth0 lines in the /etc/network/interfaces file, but I decided to stay GUI.

I'm curious as to why these network managing GUIs don't edit the /etc/network/interfaces file.  It would make more sense to me doing it that way.  Anyway, my issue is resolved, maybe this will help people in the future.

---

### Post by Iowan on 2009-04-27
> **pewp said:**
> JI'm curious as to why these network managing GUIs don't edit the /etc/network/interfaces file.  It would make more sense to me doing it that way.  Same here... but change is good - at least, not necessarily bad.  Network Manager still has some evolution, though.  Network Manager (at least what I've read about the Ibex version) keeps its configuration files in */etc/NetworkManager/nm-system-settings.conf*.

---

