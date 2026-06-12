---
title: "Cannot ping other computers on my LAN"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by jon-hjoh on 2009-01-09
Hi,

I have installed Ubuntu 8.10 on a desktop computer. This is connected to my LAN via an wireless Router (D-Link DI-524)

I can connect to internet, and also ping my routers gateway.

I want to access my Ubuntu desktop remotely (with Realvnc) from a computer running XP, but i cannot connect or ping my Ubuntu computer from the xp computer.

I have also tried to ping my XP computer from my Ubuntu computer but there is no answer.

In windows i have turned off all firewalls (Windows firewall, Symantec firewall)

The Router has no firewall enabled on the LAN side

On the Ubuntu computer, i have checked the iptables and it is equal to disabled

Chain INPUT (policy ACCEPT)
target prot opt source destination 

Chain FORWARD (policy ACCEPT)
target prot opt source destination 

Chain OUTPUT (policy ACCEPT)
target prot opt source destination

typing "sudo ufw status" tells me "not loaded"

Does anyone know anything else to be checked/disabled in ubuntu to be able to access this computer via LAN?

Thanks in Advance

---

### Post by issih on 2009-01-09
Are you pinging by ip address or hostname? ubuntu tends to need some tweaking to work with netbios (i.e. windows networking hostnames).

---

### Post by jon-hjoh on 2009-01-10
Hi, I'm pinging by ip address...

---

### Post by Iowan on 2009-01-11
Both machines are in same subnet?  Can you ping Ubuntu from XP?

---

### Post by issih on 2009-01-12
Very odd, short of some basic networking issue (like the subnet mentioned above) I'm at a bit of a loss. Worth turning off the AV and firewalls on the xp pc briefly as I know that some of them do block ping requests by default. Assuming both pcs can ping the router and access the net, its very strange that they can't see each other..

---

### Post by jon-hjoh on 2009-01-17
Hi again,

Thanks alot for Your help.
The problem was that i have a static IP for the Ethernet Card (not the wireless card) as my network printer is connected to this. I changed the /etc/network/interfaces file, so the static IP for this card would be persistent.
This worked well and I could print to this printer from my Ubuntu desktop.
The wireless network interface was managed by the network manager (the Ethernet card was not as i've changed the interface file) and for some reason this configuration could not be handled?
I removed the static IP from the Ethernet card, changed the control of the ethernet card back to the network manager and everything started to work.
I can now use VNC and share files between my computers.
The Network printer had an USB connection as well, so i have shared it by that :)

---

