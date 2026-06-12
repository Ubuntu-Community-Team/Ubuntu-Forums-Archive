---
title: "Ethernet Not Working"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by ZER01NE1NE on 2009-09-10
Hi, I'm new to Ubuntu, and so far I really like it. But I can't get my ethernet connection to work. :(

I have another computer that I'm running Ubuntu on, and the ethernet connection works just fine without any configuration. On my new computer, when I start up the computer or try to establish a connection, it tries for about a minute, then fails. It detects the device, but can't connect to it for some reason.

I'm using an ABIT-BE7 motherboard with an integrated ethernet connection. I'm running Ubuntu 9.04. I can do basic things like open the GNOME terminal and paste the output for commands, but since I'm a newbie, I don't know how to do stuff like recompile the kernel. ;)

Any help would be highly appreciated.

~ Kyle

---

### Post by Tclarkie on 2009-09-11
so ethenet is not protected

---

### Post by Tclarkie on 2009-09-11
try creating a new wired connection, that worked for me

---

### Post by ZER01NE1NE on 2009-09-11
> **Tclarkie said:**
> try creating a new wired connection, that worked for me

Let me clarify: Ubuntu finds the connection as eth0, but for some reason it tells me it's unplugged.

I tried what you said; I created a new wired connection, and now I have two, one called "Auto eth0" and one called "Wired connection 1." For Wired Connection 1 I tried leaving the mac address blank, and that didn't work. I also tried copying the mac address from eth0, and that didn't work either.

All the other motherboard devices work fine in Ubuntu, and this ethernet connection worked the last time I used it about a month ago, so unless it went bad between then and now, I don't get what the problem is. Could it be a driver problem?

---

### Post by Tclarkie on 2009-09-11
no

just go into network connections
it will open onto wired connections
create new network
then click enter.. no need to muddle with config'

---

### Post by ZER01NE1NE on 2009-09-11
OK, update:

I'm on a network with DHCP, and I was able to get the connection working with a static IP, but it absolutely won't work with DHCP. If I can set the default gateway for DHCP then I'll be good to go, because I know the default gateway. Could it be a problem with the DHCP server?

---

### Post by ZER01NE1NE on 2009-09-12
Suggestions? Anyone?

---

### Post by Iowan on 2009-09-13
Maybe you've already seen [this]("http://ubuntuforums.org/showthread.php?t=1156441") one.  Not a cure-all, but it fixed my DHCP problem.

---

### Post by ZER01NE1NE on 2009-09-15
OK, I got it working now. I don't know what happened, but now DHCP works. Hmm. But thanks anyway.

---

