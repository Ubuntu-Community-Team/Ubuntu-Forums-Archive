---
title: "Problem with VPN conneting"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by bamboorat on 2012-05-12
Hello,
I have a problem with connecting VPN
I use Windows 7, I installed both Ubuntu version 12.04 and 11.10 on VMWare Workstation 8.
I can connect to VPN in Windows 7, but I cannot connect in Ubuntu.
 
(I used same Hostname, username, and password.)

---

### Post by dwhitney67 on 2012-05-12
I've had the same problem.  I worked around the problem by setting the VM to use NAT instead of Bridged networking.  Then I setup the VPN using Win7.

From there, the VM is then part of the VPN.

---

### Post by bamboorat on 2012-05-12
I already set the network as NAT, but it doesn't work...

---

### Post by dwhitney67 on 2012-05-12
> **bamboorat said:**
> I already set the network as NAT, but it doesn't work...

Did you setup the VPN using Win7?

When you are in Ubuntu, what error, if any, do you get when you attempt to access a remote resource?  And how are you attempting to access the remote resource -- are you using telnet, SSH, Samba?

---

### Post by bamboorat on 2012-05-12
> **dwhitney67 said:**
> Did you setup the VPN using Win7?
 
When you are in Ubuntu, what error, if any, do you get when you attempt to access a remote resource? And how are you attempting to access the remote resource -- are you using telnet, SSH, Samba?
 
Now, I can connect.
I set it to use Point-to-Point encryption (MPPE).
Thank you.

---

