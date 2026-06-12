---
title: "Does Ubuntu has firewall settings"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by bruce1914 on 2008-12-14
I have installed Ubuntu 8.10 with default setting and packages. There seems to be no firewall. However, when I opened a vncserver in my Ubuntu and tried to access from a local-network computer, it fails. What's more, I have write some program using C and try to make a connection via TCP/IP between my Ubuntu and a local-network Red Hat AS3 computer, it failes also.
All of these seems to be the network port problem. Is there any program in Ubuntu 8.10 that would act as a firewall to disable connections from unauthorized port?
--
Thanks in advance!

---

### Post by superprash2003 on 2008-12-14
iptables is default firewall for linux.. in the terminal type sudo iptables -L .. to list firewall rules..

---

### Post by bruce1914 on 2008-12-15
I tried and it prints this:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

Anything wrong?

---

### Post by bruce1914 on 2008-12-15
I have googled for 'iptabls' command and it says that my setting is eqaul to disable firewall. Therefore, is there other things wrong?

---

### Post by mdhunn on 2008-12-16
Ubuntu uses ufw to configure the firewall.  However I found out while noodling around with my laptop that it is not enabled by default.:mad:

To enable the firewall open a terminal and type:
[FONT="Courier New"]sudo ufw enable[/FONT]

Further info can be found in ufw's man page.  In a terminal type:

[FONT="Courier New"]man ufw[/FONT]

You might also want to look into installing Firestarter.  It's a GUI for configuring linux firewall that provides real time status.  But be advised that it isn't too smart about switching network interfaces, ie wireless at a coffee shop and wired at home.  So it's not the ideal solution for laptops, but I haven't found a better one yet.  I haven't looked into how smart ufw is about dealing with laptops though.

---

### Post by bruce1914 on 2008-12-26
Thanks.

I have tried 'ufw' and it is closed already.

My problem is that I do not want any firewall but there seems to be one running in default when I have installed Ubuntu 8.10.

Is there a one in default?

---

