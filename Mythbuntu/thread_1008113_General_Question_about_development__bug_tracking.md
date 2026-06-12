---
title: "General Question about development / bug tracking"
date: 2008-12-11
forum: Mythbuntu
---

### Post by NTBlade on 2008-12-11
Hi all, first post here.
This is my fist experience with Mythbuntu but I'm sorry to say it's not all been positive.  I've installed both the 8.10 i386 and AMD64 versions on an opteron server and so far both exhibit the same infuriating bugs:

The network manager just doesn't allow a static IP address to be set.  (Doesn't survive a reboot).

The Diskless client install doesn't work in that the DHCP server doesn't appear to be installed.

Now please don't think I'm being negative.  This myth-centric distro has great potential but these seem like quite serious bugs to have slipped through into release.  I've looked in:
[https://bugs.launchpad.net/mythbuntu/8.10/+bugs](https://bugs.launchpad.net/mythbuntu/8.10/+bugs)
but there's nothing reported there.  Are there really no bugs at all or am I looking in the wrong place?
I've searched the forums and there's no real resolution to these problems.

Oh, I've looked again but nothing about the above.  Am I the first to experience this?

I'm not able to develop but I can help withesting and resolving these issues.  Please don't think I'm ranting, I'm just not getting a great feeling from this.

Regards,
NTB

---

### Post by SiHa on 2008-12-11
To be fair 8.10 has only been around a for a couple of months. I'm surprised it has no bugs listed though!
Have you tried 8.04.1? I believe this is more stable - it's what I'm using.

---

### Post by NTBlade on 2008-12-12
Thanks for the reply,
The reason I'm using 8.10 is that I read that it supports my tuner "out of the box" (Nova-TD 500) although the remote doesn't work but this if going to be a headless backend anyway.  I'll go and report these issues as bugs abd see what happens.

NTB

---

### Post by ian dobson on 2008-12-12
Hi,

on my frontend I jusr got rid of network manager and manually configured a fixed IP address from the terminal by editing the /etc/network/interfaces.

Athough I'm getting used to graphical interfaces I still feel happier with a text terminal.

Regards
Ian Dobson

---

