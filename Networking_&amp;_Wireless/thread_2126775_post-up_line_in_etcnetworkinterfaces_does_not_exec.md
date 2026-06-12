---
title: "post-up line in /etc/network/interfaces does not execute on boot"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by deepdive on 2013-03-18
I have an Ubuntu server 12.04

/etc/network/interface file defines eth0 as follow. When the system comes up the interface gets configured properly, however neither the /etc/resolv.conf files get populated, nor the post-up line gets run

auto eth0
iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        gateway 192.168.1.1
        network 192.168.1.0
        broadcast 192.168.1.255
        dns-nameservers 192.168.1.1
        dns-search xyz.com
        up ip route add 192.168.1.0/24 dev eth0
        post-up /sbin/iptables-restore < /etc/iptables.up.rules

after the system comes up, if I run the "/sbin/iptables-restore < /etc/iptables.up.rules" by hand the firewall gets configured and everything works like a charm. But not automatically by the if-up script when the system boots up. Similarly the resolvconf (8) does not set up the /etc/resolv.conf file.

What could be wrong here?

thanks

---

### Post by jdthood on 2013-03-20
Try putting "/sbin/iptables-restore < /etc/iptables.up.rules" into a script and run that script from the "post-up" line.

---

### Post by deepdive on 2013-03-22
Tried that. But still no luck.

Any way to debug this to figure out exactly where the problem lies? Should I put debugging code into if-up ?

---

### Post by Doug S on 2013-03-22
I wonder if your post-up stuff is actually running properly but then if something comes along later and clobbers what was done.
As a sanity check maybe add some sort of indicator to the script. Here is an example I just did on one of my computers:```
doug@test-smy:~$ [COLOR=#ff0000]cat /etc/network/interfaces[/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet dhcp
[COLOR=#ff0000]post-up /home/doug/test_post_up[/COLOR]
``````
doug@test-smy:~$ [COLOR=#ff0000]cat test_post_up[/COLOR]
#!/bin/dash
date >> /home/doug/test_post_up_data
``````
doug@test-smy:~$ [COLOR=#ff0000]cat test_post_up_data[/COLOR]
Fri Mar 22 09:01:52 PDT 2013
```So, I know that my post-up script was executed. 
You can also look at the files in /var/log for any clues, although I don't find anything for my other computer where I do run a significant script via a pre-up directive.

---

