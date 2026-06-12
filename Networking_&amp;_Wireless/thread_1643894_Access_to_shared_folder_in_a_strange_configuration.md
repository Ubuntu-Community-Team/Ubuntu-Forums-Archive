---
title: "Access to shared folder in a strange configuration"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by Debie on 2010-12-12
Hi all,
I've a question about a connection to a shared folder on a pc behind an ubuntu 10.04 server.
The Ubuntu machine itself is behind a Cisco router.
Cisco router has a nat 1-to-1 to Ubuntu machine with the static public ip x.y.x.z
The Ubuntu machine has one only interfaces eth0 bridged with a virtual tap0 in the virtual br0 interface.
This because on the Ubuntu machine is running OpenVPN in bridged mode.
I want to reach a private share on the host 192.168.100.2 using the x.y.w.z static IP.
Is that possibile?
Ubuntu machine has no firewall running (I was not able to run shorewall firewall for now).
Any suggestion?
Thanks,

Debie

---

### Post by Debie on 2010-12-13
Anyone? ):P

---

