---
title: "Network connection, but no Internet access"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by Gandalf_the_Grey on 2010-02-05
I am attempting to connect Ubuntu 9.10 to the Internet.  I have a network connection, and Karmic detects it fine.  I can ping addresses within our network (e.g. the Windows computer in the next room), and I can ping the router, but if I ping, say [www.google.com](www.google.com), it says "Destination Net Unreachable".  Previously, in Jaunty, I had a similar problem.  I found a workaround: launch Pidgin.  Somehow, launching Pidgin temporarily edits my configuration.  However, in Karmic, I have no access to Pidgin, however, and Empathy does not do the same thing. Since I have no Internet, I cannot "sudo apt-get install" anything.  How can I get the Internet working?

---

### Post by chili555 on 2010-02-05
The classical answer is that it's nameserver problem. Take a look at:```
cat /etc/resolv.conf
```It may be empty, misconfigured or non-existent. I would start by amending it to:```
nameserver 192.168.x.x
```Use the address of the router. If other computers on the same router get to the internet, then you know the router has usable DNS nameservers.

---

### Post by Iowan on 2010-02-05
Can you ping Google by address (74.125.95.99 might be one)? OpenDNS server (208.67.222.222)? You might also check **route -n** to verify your gateway. Does machine get address via DHCP? You can add nameservers via */etc/dhclient.conf* "prepend" line.

---

### Post by Gandalf_the_Grey on 2010-02-06
Found a solution to my own problem, it would seem.  It was IPv6 that was causing the problem.  Our router is of an older generation and doesn't support IPv6.  Disabling it in the /etc/modprobe.d/aliases file by adding the lines:

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off

caused ping [www.google.com](www.google.com) to work and Internet to become available again.

---

### Post by das.war on 2010-02-06
[SIZE=5][SIZE=3]i am having similar problem with wireless setup..... network got established...... but no internet access 

able to connect to 192.168.1.1

but  not to google.com or any other site[/SIZE]  




[/SIZE]

---

### Post by Gandalf_the_Grey on 2010-02-06
Go into the Terminal, and enter "sudo gedit /etc/modprobe.d/aliases", then add the three lines I mentioned above, then reboot.

---

