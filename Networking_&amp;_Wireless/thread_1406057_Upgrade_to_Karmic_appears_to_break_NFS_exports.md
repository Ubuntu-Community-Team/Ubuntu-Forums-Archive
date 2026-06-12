---
title: "Upgrade to Karmic appears to break NFS exports"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by redhorse on 2010-02-13
I've spent the last two days googling for answers, but haven't been able to find any solutions related to my situation (though there appear to be related questions).

I have four PCs, all running Karmic.  Three were installed from scratch on a clean hard drive a few weeks ago (2x amd64, 1x i386), one was upgraded from Jaunty two days ago (amd64).

On all four PCs I have the Public directory exported to a range of LAN addresses in /etc/exports and I have NFS installed and working on all four systems.

Before upgrading the Jaunty machine to Karmic, everything was working fine.  All four PCs could mount each other's Public directories.

After upgrading the Jaunty machine to Karmic, the former Jaunty machine can still mount everyone else's Public directories, but none of the other Karmic machines can mount the formerly Jaunty machine's Public directory.  The mount command simply hangs and I have to do a control-C to get it to stop (mounting via fstab or mount command have the same result).  The other machines are able to successfully ping the formerly Jaunty machine just fine.

On the formerly Jaunty machine, I've done an nfs-kernel-server restart, an exportfs, and a full reboot.  Nothing seems to fix the problem.  dmesg shows nothing at all from the mount attempt on the "clients", and on the formerly Jaunty machine it shows some network traffic info (Inbound IN=eth0 OUT= MAC=...) but that's it.  Without any error messages of any kind, I'm at a loss as to what might be happening.

Based on what I am seeing, a full clean install of Karmic works just fine, but the upgrade from Jaunty breaks something related to NFS exports.
Since I've reached the end of my knowledge regarding NFS and Google hasn't helped, does anyone out there have any ideas on what else I might try?

---

### Post by redhorse on 2010-02-14
Some more information...

I tried the mount command again, but let it go on for over a minute.  Eventually it came back with "mount.nfs: mount system call failed".

Now dmesg gives me: rpcbind: server *formerjauntymachine* not responding, timed out.

Now I have something to go on...

---

### Post by redhorse on 2010-02-14
OK, I'm an idiot. ;)

It has been so long since I've done anything to my firewall that I forgot to look at that.  Names of my machines have changed, which needed to be changed via Firestarter.   I should have listed them by IP address (if possible) instead...

---

