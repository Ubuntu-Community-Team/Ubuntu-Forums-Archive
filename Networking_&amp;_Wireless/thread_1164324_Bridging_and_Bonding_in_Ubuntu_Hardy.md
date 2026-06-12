---
title: "Bridging and Bonding in Ubuntu Hardy"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by cmeiklejohn on 2009-05-19
I'm having some trouble getting bridging and bonding working in Ubuntu Hardy.  I'm seeing this behavior with both the Xen kernel, and the non-Xen kernel. 

I've tried about 10 different configurations, and posted below is the latest.

auto br0
iface br0 inet static
address 10.0.1.27
gateway 10.0.1.1
network 10.0.0.0
netmask 255.255.0.0
pre-up /sbin/ifconfig eth0 up
pre-up /sbin/ifconfig eth1 up
pre-up /sbin/ifconfig bond0 up
pre-up /sbin/ifenslave bond0 eth0
pre-up /sbin/ifenslave bond0 eth1
pre-up /usr/sbin/brctl addbr br0
pre-up /usr/sbin/brctl addif br0 bond0
pre-up /usr/sbin/brctl stp br0 off
pre-up /usr/sbin/brctl setfd br0 0

When the system boots, it has no connectivity at all.  If I remove the bridge and set the IP on bond0, then connectivity is fine.  Bridging also works if I configure it for eth0 alone.  So, in summary, both components work fine independently, but as soon as I put a bridge on bond0, I lose all connectivity.

Any advice?

Thanks,
Chris

---

### Post by cmeiklejohn on 2009-05-19
*nudge*

---

### Post by superprash2003 on 2009-05-20
are you trying to do something similar to internet connection sharing ( ICS)?

---

### Post by cmeiklejohn on 2009-05-20
No, I'm working on getting Xen virtualization.  The Xen scripts were not working to bring the bridge up, so I'm attempting to set the bridge up ahead of time through the OS, while it boots.

I have Xen virtualization working with bridging and bonding on Ubuntu Feisty, but something in Hardy is not working.  I tried searching the bug tracker for anything that might be related, but I couldn't come up with anything.

---

### Post by cmeiklejohn on 2009-05-20
The latest thing I have discovered is that when I enable the bridge, my catalyst switch reports that line protocol has gone down on both ethernet interfaces.

---

### Post by jinzishuai on 2009-06-01
Hi

Have you got it working?
I am working on similar issues of briding+bonding for the virtualization purpose. Please let me know if you find a solution.

Thanks.

Shi

---

### Post by jinzishuai on 2009-06-01
This post helps me a lot:
[http://ubuntuforums.org/showthread.php?t=835732&highlight=bonding+bridge](http://ubuntuforums.org/showthread.php?t=835732&highlight=bonding+bridge)

---

