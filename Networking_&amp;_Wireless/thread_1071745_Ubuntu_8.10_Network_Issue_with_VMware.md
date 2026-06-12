---
title: "Ubuntu 8.10 Network Issue with VMware"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by lopy_is_me on 2009-02-16
Hi all
I am a user of ubuntu from a long time and recently tried ubuntu 8.10 on my laptop and It was Amazing and a friend of mine tried it but on Vmware WorkStation ACE Edition 6.0.2 on windows cause he is an Oracle Database Developer and heard that developing under linux is better that windows and he liked it but there is a problem there is a problem that he can't setup the LAN settings and I tried hard to but I can't make Ubuntu read the LAN and connect to the internet and the network
Please Could you help me

---

### Post by lopy_is_me on 2009-02-18
Come One guys I need HElp

---

### Post by smc18 on 2009-02-18
If your running Virtual Machines you can configure the virtual ethernet interface to be bridged so that you can configure the virtual NIC as if it were a separate pc on the lan, or you can set it up to share the IP address with the host machine, using NAT.

Now, I've never set a vm using NAT, but making it bridged should work for what you need.


Do you know how your friend has it set up?

---

### Post by smc18 on 2009-02-18
This would be done in the Virtual Machine Settings, before you even power-on the VM and try to configure it from within the OS.

---

