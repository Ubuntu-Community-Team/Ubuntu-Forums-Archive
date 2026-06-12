---
title: "killing 'named'"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by stimpack on 2006-05-30
Hi all. I recently installed network-manager into my Kubuntu-breezy box after really liking it in my Ubuntu-Dapper laptop.

My internet stopped working so I uninstalled network-manager and now all is fine, except 'named' is running. I dont want to run a DNS server, I am quite happy using my ISPs one.

My question is, (as the title probably suggested long before the body), how to I remove 'named' and it is safe to do so now?.

---

### Post by Iowan on 2006-05-30
There's the **kill** command, but there may be a more elegant way (diald stop?).  You may need to turn off **diald** under Administration - or by manually editing the startup files - to prevent it firing back up on next reboot.

---

### Post by stimpack on 2006-05-30
Thanks, but diald is not installed. And yes I need somthing more permanent than kill. I cannot find out where it is launched. I might just delete it from /usr/sbin and hope it doesnt break anything :).

---

### Post by lkagan on 2006-05-30
The great thing about package managers is that when you remove an application with the package manager, it also removes/disables the configuration. So if you wish to remove the application as your post suggests, simply remove it with Synaptic or apt-get. First you have to find out which DNS package you have installed. I think named is bind9. Check if bind9 is installed by running 
```
dpkg -l bind9
```
If that's it, simplty use
```
apt-get remove bind9
```
I hope this helps.

Larry

---

### Post by Iowan on 2006-05-30
[QUOTE=stimpack]Thanks, but diald is not installed. And yes I need somthing more permanent than kill. I cannot find out where it is launched. I might just delete it from /usr/sbin and hope it doesnt break anything :).[/QUOTE]OOPS!!! Brain was thinking **named** (or bind), but fingers typed **diald**.  I like the suggestion to remove it (rather than just disable it as I'd have suggested)...

---

