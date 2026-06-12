---
title: "VPN Can't connect to internet"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by MediocreGopher on 2010-09-16
Sorry if this is a basic question with an obvious answer. I'm pretty sure the reason this isn't working is because I don't quite understand what I'm doing, but here goes:

I've got a remote ubuntu machine with an openvpn server on it, and I am connecting to it with my laptop (also ubuntu 10) using the gnome network manager. I can connect to the vpn fine; my laptop gets assigned an ip address with the virtual lan and I can ping the server using its virtual ip address. However, once connected I am not able to reach any machines outside the virtual network (aka, the rest of the internet). Am I simply not understanding what it is I can/can't do with a vpn? Or have I not fully set up the server (I used the guide on OpenVPN's website to set it up).

Thanks!

---

### Post by SeijiSensei on 2010-09-17
Sounds like a routing problem to me.  After you've got the VPN running, open a terminal and type "/sbin/route -n" at the prompt.  If the "default" route (0.0.0.0) points to the remote VPN host, that's the problem.  

Now, usually, OpenVPN doesn't repoint the default route but simply sets up a point-to-point connection between the tunneled hosts.  In the configuration file for OpenVPN, do you have an "up" parameter specified that runs a routing script of some kind, or a "route" parameter?  If so, comment those out by putting a hash mark ("#") at the beginning of the line and restart the tunnel.  If you're still having problems, open a terminal window and type the command "/sbin/route -n" at the prompt.  Where does the route for 0.0.0.0 at the bottom of the list point to?

Here's a snippet from the routing table on one of my machines:

```
10.1.0.1        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
0.0.0.0         A.B.C.D         0.0.0.0         UG    0      0        0 eth0

```
where "A.B.C.D" is the address of my ISP's upstream router.  This tells the kernel to send packets for 10.1.0.1 via the tunnel, but everything else goes to my ISP.

---

