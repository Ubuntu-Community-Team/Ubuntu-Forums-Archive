---
title: "Reverse ethernet cable setting between 2 ubuntu"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by Browser_ice on 2010-07-27
I have a reverse ethernet cable and I want to use it to connect a desktop 10.04 Lucid + laptop 10.04 Lucid

How do I do this ?  I have no routers, no hubs.

This is so I can transfer HD ISO backup files.

---

### Post by Iowan on 2010-07-28
Presuming "reverse ethernet cable" is a crossover cable, you'll need to set up IP's on each machine in the same subnet. That's what "**link-local**" is supposed to do (but I haven't really tried it). Once you get networking established, you'll need to choose a file-sharing method. Samba, NFS, SSHFS, and FTP are all options - you'll need to install the server on the machine with the files you wish to transfer (or both - if you plan to transfer both ways). There are links/How-To's available for the filesystems - when you decide which you prefer.

---

### Post by Browser_ice on 2010-09-04
> **Iowan said:**
> Presuming "reverse ethernet cable" is a crossover cable, you'll need to set up IP's on each machine in the same subnet. That's what "**link-local**" is supposed to do (but I haven't really tried it). Once you get networking established, you'll need to choose a file-sharing method. Samba, NFS, SSHFS, and FTP are all options - you'll need to install the server on the machine with the files you wish to transfer (or both - if you plan to transfer both ways). There are links/How-To's available for the filesystems - when you decide which you prefer.

**I need a step by step explanation on how to do this. **

I checked the [zeroconfnetworking]("https://wiki.ubuntu.com/ZeroConfNetworking") page but it is not noob friendly for its implementation. I don't even know if I need this or not to achieve what I want to do: cross-wire between 10.04 laptop and 10.04 desktop.

I looked at network manager to add a connection but could not figure it out.

I want to do this so I can transfer backup images of my laptop to my desktop. Money is a problem.

Also, will this interfere with my normal internet connection ?  I want this to be totally transparent. Meaning, when I plug back the normal ethernet cable to have access to Internet, I have automatically access to internet. When I plug back the cross wire, I have automatically access to my laptop. I do not want to keep doing setups every times i switch cables.

I will try a few things then come back here for any possible answer.

---

### Post by Browser_ice on 2010-09-06
Anyone ?

---

### Post by Browser_ice on 2010-09-10
Anyone ?

---

### Post by Hobgoblin on 2010-09-10
> **Browser_ice said:**
> [B]
Also, will this interfere with my normal internet connection ?  I want this to be totally transparent. Meaning, when I plug back the normal ethernet cable to have access to Internet, I have automatically access to internet. When I plug back the cross wire, I have automatically access to my laptop. I do not want to keep doing setups every times i switch cables.


No, it won't be automatic.  You will have to set up the network each time.

Since your internet is supplied via ethernet, are you connected to a router?  If so it would be much simpler to connect both to the router and set up file sharing in the normal way.  There is no advantage to connecting the two directly.

---

