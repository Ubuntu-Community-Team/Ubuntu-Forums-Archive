---
title: "Network icon not showing up after making the ip static"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by Bobi86 on 2011-03-03
Hi all,
          I'm using Ubuntu 10.04 LTS - the Lucid Lynx.

I intended to make my IP static by opening the file network interfaces "sudo gedit /etc/network/interfaces"
and adding the following 
"auto eth1
iface eth1 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
"
and then restarting the network "sudo /etc/init.d/networking restart"
The static ip setting is successful except for the warning "warning produced: SIOCDELRT: No such process"
When i enquire for ifconfig the ip was set static to 192.168.1.100 and i was connected to the internet and everything works fine.
But when i restart the system the network icon at the right top corner disappears and am not able to get connected to the internet.

And when i remove the block of code mentioned above and restarted my system, everything works fine.
How can i make my ip static? What is preventing my static ip configuration.

Someone please throw some light upon this.

Regards,
Balaji Radhakrishnan

---

### Post by sikander3786 on 2011-03-03
I think while using your /etc/network/interfaces file for configuring the network, you won't see the Network Manager in notification area. If you want to use network manager, you need to _use_ network manager for static ip configuration.

Restore your interfaces file to defaults and right click the network icon in notification area > Edit Connections > Auto ethx > Edit > IPv4 Settings > Manual > Add.

---

### Post by YesWeCan on 2011-03-03
Right.
You may be able to connect to the internet if you use an IP address. It may be that its missing DNS info. The better way to set a static address is in your router, that way the router assigns the address and the DNS routes.

---

### Post by Bobi86 on 2011-03-06
Yup... i got it fixed that way... (as suggested by [sikander3786]("http://ubuntuforums.org/member.php?u=806649"))
But could any 1 tel me y this dint work the way i did?

---

