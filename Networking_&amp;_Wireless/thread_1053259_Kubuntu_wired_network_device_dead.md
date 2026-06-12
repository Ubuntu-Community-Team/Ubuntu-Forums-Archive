---
title: "Kubuntu wired network device dead"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by paroch on 2009-01-28
**Problem description:** Wired Network not working after a bad mistake involving a chmod at root level.

The network devices (eth0 and eth1) appear in the network manager, but they do not connect to anything.
From what i can tell, the problem is exclusively software - but i don't know enough command line to fix it, and the KDE network manager is useless.

All hardware is working, tested with other machine - cable is tested, network port is tested, modem is tested.

**Attempted fixes:** Messed around with the KDE network manager, enabling/disabling the network devices.

**Recent changes:** Yup - "sudo chown -R [local user]:[local group] / " by mistake.
Of course, this removed my "sudo" rights completely - "sudo: must be setuid root" (i need sudo rights to run some apps).

Booted with LiveCD, didn't know the original permissions so i could carefully revert them one by one, so i just chown-ed everything to root.

Restarted, couldn't get in to desktop - realised i'm _stupid_, booted again with LiveCD, and chown-ed the local user's home folder back to "[local user]:[local group]".

Restarted again, sudo rights are back, every app seems to be running properly - except for the network, which is completely dead.

I presume some network device or service or something like that needed different permissions, and was stopped or killed when booting without them, and now that the permissions seem to be fixed, i need to start something manually.
Problem is, i don't know what to start manually, or how.

--

**Operating system:** Kubuntu Linux 8.10, 32bit.

**I have Googled and searched the forums:** Yes - it doesn't seem that there's any easily found solution to this on Google, so i posted here, maybe some guru knows how to fix it...

---

### Post by nixscripter on 2009-01-28
The only solution I know of to **sudo chown -R /** is the same as **sudo rm -r /**: restore from a backup. If you don't keep them, I assume you will start today. ;-)

Anyway, as for your problem. First question with a dead network connection is what the hardware is doing. Type **sudo ethtool eth0** into a terminal, and post the result (don't forget [code] blocks).

---

### Post by paroch on 2009-01-29
> **nixscripter said:**
> The only solution I know of to **sudo chown -R /** is the same as **sudo rm -r /**: restore from a backup. If you don't keep them, I assume you will start today. ;-)

Anyway, as for your problem. First question with a dead network connection is what the hardware is doing. Type **sudo ethtool eth0** into a terminal, and post the result (don't forget [code] blocks).

Nevermind - apparently this is only the most visible problem on the system.

Most stuff doesn't seem to have permissions to run anymore.

I could revert each one, one by one, but the install is fairly fresh, and i managed to back up all my personal files in there, so i'm just reinstalling.

---

### Post by nixscripter on 2009-01-29
That's probably the best solution.

Please mark this thread as solved (under the Thread Tools menu).

---

### Post by paroch on 2009-01-30
> **nixscripter said:**
> That's probably the best solution.

Please mark this thread as solved (under the Thread Tools menu).

Can't, don't have any option to do that under Thread Tools.

---

