---
title: "SSH stopped responding"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by williane on 2009-02-25
I setup a Hardy server at home a few days ago on an old system. Ran fine for 2-3 days. I have it set up with irssi running in screen so I can SSH in from work/laptop/etc.

I am using dyndns because I don't have a static IP. I set everything up using a couple of tutorials I found online. Set my router up to use dyndns, and set a static IP on my local network. 

Starting yesterday afternoon I am for some reason unable to SSH in anymore. It tries to connect for a couple min. then gives me:

ssh: connect to host *myhost*.dyndns.org port *myport#*: Connection timed out

The computer is still running fine. I can log in locally and irssi is still connected.

I have tried changing the port and restarting SSH but still no luck.

Anyone have any ideas on what happened?

Thanks in advance.

---

### Post by williane on 2009-02-25
Think I figured it out. The static local IP I had set wasn't in the valid range for the router (maybe this doesnt matter, the router is using DHCP but the box isnt. im kinda nub to networking) and it had changed the IP on the box. So I changed the IP, reserved that IP in the router settings to the MAC address of the ubuntu server, and restarted init.d/networking. 

At least its working again for the moment. I guess I'll see in another couple of days if it tries to change the IP again.

---

### Post by Iowan on 2009-02-25
Check your router setup - you *might* be able to set up a static (fixed) lease based on server's MAC address. Server would be set to get address via DHCP - router would issue it the same one each time.  This address WOULD need to be outside the address pool.

---

### Post by williane on 2009-02-25
Hmm, I tried that but it told me I had to use one in the pool. So I did and it worked. Although this was just to reserve a certain IP for that MAC address, maybe you're referring to something else?

---

### Post by Iowan on 2009-02-25
Use what works - your router DHCP has different requirements than my DHCP server.  I use DHCP3 on an Ubuntu server - from the /etc/dhcp3/dhcpd.conf file:> # Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
 I'd check my modem, but I'd have to enable the server, and that'd probably play havoc with the network. (Maybe later...)

BTW, the address pool is *probably* different than the subnet - the address WOULD need to be in the same subnet.

---

