---
title: "Parental control DHCP server"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by oh6fse on 2013-05-10
Hi i have dhcp wich is running ubuntu and i want control web ussage per day for some ips and block them when i want without going to ssh and making complex scripts.  is there some programs using web panel to be easy too use? also i'd like to set max bandwith usage to some ips on  my dhcp server
i tried google without any luck. controling also only LAN.
example:


internet---dhcp server(ubuntu 12.04)--dummy router---computers some have parential control some havent

---

### Post by TheFu on 2013-05-10
Dan's Guardian?  Hopefully the maintainer will see this and respond with more details.

---

### Post by oh6fse on 2013-05-12
yeah but it should be easy to use like router softwares ex.web admin.
Because everybody in my family cant use ssh or console :lolflag:

---

### Post by TheFu on 2013-05-12
You need a box that can be dedicated to this purpose. I don't see why anyone other than you would need to know about ssh.  Only the main gateway/firewall/proxy machine should need any configuration. All the other machines shouldn't need any manual configuration - automatic configs from the DHCP server should handle everything else if you deploy a transparent proxy server.

[http://ubuntuforums.org/showthread.php?t=826202](http://ubuntuforums.org/showthread.php?t=826202) might be helpful with some ideas. It is a little old, but the comments are still relevant.

I recently deployed a dedicated pfSense solution at a small network - only about 50 end-user machines.  All point-n-click configuration for everything, but more complex than an average home user without a networking background will understand.  A GUI doesn't make things easier.

---

