---
title: "IP allocation DHCP bug in VirtualBox 4.0.4?"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by SteveCut on 2011-05-29
I've set up VirtualBox to host an XP guest. I have DHCP enabled in the VirtualBox settings. When I start XP in VirtualBox, the internal DHCP server should assign an internal network (vboxnet0) IP address. It doesn't. 'ifconfig -a' shows no 'inet addr' and I cannot access the vboxnet0 Virtualbox network from my XP guest OS. I've tried using the VBoxManage CLI to enable DHCP too. That also doesn't work.

The workaround is as follows:  when starting Virtualbox for the first time in a session, select 'File>Preferences>Network and edit the host only network to disable the DHCP Server. Click OK>OK to close the dialogs. Then repeat the process to enable the DHCP server again. This time DHCP really is enabled and the network IP will be available. In Terminal, you can confirm this with 'ifconfig -a.'

Doing a '--disable' followed by a '--enable' from the VBoxManage CLI may also work. but I haven't tested this.

I'm new to Ubuntu so I may be missing something, but this looks like a bug to me.

---

