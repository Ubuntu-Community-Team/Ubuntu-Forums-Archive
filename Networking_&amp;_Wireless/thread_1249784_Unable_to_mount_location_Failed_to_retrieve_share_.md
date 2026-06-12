---
title: "Unable to mount location: Failed to retrieve share list from server"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by beatlesfan94 on 2009-08-25
What am I doing wrong? I'm trying to connect two Ubuntu computers together. One is a desktop connected to a router through a wire. The other is a laptop connected to the network via wireless. Both are running 9.04.

Whenever I try to connect from either computer, I get the error message: "Failure to mount location. Failed to retrieve share list from server." I installed Samba and nautilus-share.

Oh, and is it supposed to say Windows network, even though it's technically between two Ubuntu computers?

---

### Post by Iowan on 2009-08-25
Have you installed Samba-server on one/both machine(s)? If so, do you have firewall(s) active?

(Belated clarification) Ubuntu comes with clients for several protocols, but the server must be installed separately.

---

### Post by beatlesfan94 on 2009-08-25
> **Iowan said:**
> Have you installed Samba-server on one/both machine(s)? If so, do you have firewall(s) active?
I have the samba package installed, but not anything called samba-server. :/
And I don't have firewalls active. Just my router, I guess.

---

### Post by dmizer on 2009-08-25
> **beatlesfan94 said:**
> I'm trying to connect two Ubuntu computers together.

Forget samba and use NFS instead. Please see the 4th link in my sig.

---

### Post by fela on 2009-08-25
> **dmizer said:**
> Forget samba and use NFS instead. Please see the 4th link in my sig.

+100. Only ever use samba if you use windows, and only then if you absolutely have to. It's a pain in the butt from my experience, especially on non-samba-native OSes such as *nix.

---

