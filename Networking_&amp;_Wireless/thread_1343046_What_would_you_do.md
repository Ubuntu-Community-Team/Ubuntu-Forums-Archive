---
title: "What would you do?"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by ZarathustraDK on 2009-12-01
Here's an annoying question that has been bothering me.

**What you are/can/can't.**
You're a support-center which provide desktop-support to pc's on remote networks consisting of Linux-pc's. (read: you can't VNC to an IP like on an internal network because of router/server/whatever blocking the entrance to the other end).

You can't mess around with the router on a location, as it would take a lot of time because there are many locations.

You got a server on your internal network with an external IP you can mess around with/utilize to solve the problem.

You can decide what goes on the linux-boxes on the remote locations, since they're not set up yet.

You would like to stay clear of commercial software.

**The Question**
How do you provide remote desktop support to the Linux-boxen on the remote network given the above-mentioned circumstances:?:

---

### Post by pookiebear on 2009-12-01
logmein's linux host was supposed to be available this quarter.
Also showmypc.com was supposed to have theirs available. 
gotoassist has no linux suppoort yet.
gotomypc no linux.

You might be able to build a tightvnc server for the clients to connect to when there is trouble. Someone else might chime in with better options this is all I can think of at the moment.

---

### Post by lykwydchykyn on 2009-12-01
Don't ask me for details, because the concept makes my head spin a little, but in theory couldn't you set up a reverse ssh tunnel from the clients to the server, then tunnel back through them to run the "remote desktop" solution of your choice (NX, VNC, XDMCP, etc)?

Granted, it'd probably be a bit slow over a WAN.

---

### Post by Excedio on 2009-12-01
You could try [NoMachine]("http://www.nomachine.com/"). Not sure if these Linux boxes you speak of are headless servers, or work stations, but you are not going to see a live desktop from the other end if that's what you're after.
 
It's going to show you a virtual image of the desktop at the other end.

---

### Post by ZarathustraDK on 2009-12-02
> **lykwydchykyn said:**
> Don't ask me for details, because the concept makes my head spin a little, but in theory couldn't you set up a reverse ssh tunnel from the clients to the server, then tunnel back through them to run the "remote desktop" solution of your choice (NX, VNC, XDMCP, etc)?

Granted, it'd probably be a bit slow over a WAN.

This was gold for me. Yeah, this really seems like the way to go, strange I haven't seen any apps that anywhere.

So as I see it, you got 3 communication points:

1. The remote, off-network computer. On it there'll be a bash-script that the user can click. The bash-script will establish a reverse SSH-tunnel between the support-company's server on port X and the users computer on port 5900 (or whatever port the VNC-server on the remote-computer listens to).

2. The server. It's only role is to act as an external hook for remote reverse SSH-tunnels initiated by the users.

3. The on-network support-pc. Uses a VNC-client to connect to port X on the server, thereby gaining access to port 5900 on the remote users pc, aka VNC'ing to the remote pc, which is what we want.

Only requirement is that the router on the remote location allows for traffic on port 5900/ssh-port (not sure about this, so please correct me if I'm wrong).

Of course this method only allows for one connection, so I'll have to figure out a script (on the remote end) that picks an open port out of a variable range of available ports on the server, then makes a popup saying something like "Connected to port 9965" which the user can then tell the supporter over the phone.
That's easy support. Really, it's easier than our current system of punching in IP's/hostnames manually in Dameware on XP. Click a button and tell the support-guy a number. :P

---

### Post by lykwydchykyn on 2009-12-02
> **ZarathustraDK said:**
> Only requirement is that the router on the remote location allows for traffic on port 5900/ssh-port (not sure about this, so please correct me if I'm wrong).


No, that's the point of the reverse tunnel -- the router only needs to allow the workstation to make an outgoing ssh connection to the server.

---

### Post by koenn on 2009-12-02
> **lykwydchykyn said:**
> Don't ask me for details, because the concept makes my head spin a little, but in theory couldn't you set up a reverse ssh tunnel from the clients to the server, then tunnel back through them to run the "remote desktop" solution of your choice (NX, VNC, XDMCP, etc)?

Granted, it'd probably be a bit slow over a WAN.

something like that, but I'd consider doing it with openvpn.

You set up openvpn on all the "clients". possibly using tcp, client-mode. So they'll set up the tunnel - no NAT trouble on the far side
This means all clients will have a direct, secure network connection to your vpn server. You can control those tunnels with a firewall on your end - eg block all traffic through the tunnel unless someone needs assistance, only allow communication (through the tunnel) if it's initiated at your end, etc.


Any remote interaction with them can go through that tunnel, initiated from your side, so you have a choice : ssh, ssh -X, rdp/vnc solutions, ... depending on the needs of the moment.

You may need a small thingy where the user can see the IP address of its tun interface so he can tell you where to connect to. 

Haven't done this, but it'll probably work.

---

### Post by ZarathustraDK on 2009-12-14
We've gotten a bit further with out test-setup.

We can establish a reverse ssh-tunnel from the remote user-pc (as in Server ---ssh---> User), and vnc from the server to the user via the tunnel.

Problem is, we can ONLY vnc from the server itself; we can't vnc from an in-house support-pc to the specified port on the server that connects to the remote user-pc.

Any ideas what we're doing wrong?

---

### Post by koenn on 2009-12-14
> **ZarathustraDK said:**
> We've gotten a bit further with out test-setup.

We can establish a reverse ssh-tunnel from the remote user-pc (as in Server ---ssh---> User), and vnc from the server to the user via the tunnel.

Problem is, we can ONLY vnc from the server itself; we can't vnc from an in-house support-pc to the specified port on the server that connects to the remote user-pc.

Any ideas what we're doing wrong?
This is why I suggested openvpn : it builds a tunnel at network (IP) level, so it's trivial to set up routes through that tunnel and allow other PC's on a connected LAN to use it. Pretty standard network administration. 

with ssh tunnels, your one lever higher up, at TCP-level, so routing doesn't work there.
You can probably work around it by setting up additional ssh tunnels to connect to the forwarded port on the server, from other PC's on your LAN - maybe something with "local" and "remote" tunnels
Never done that, so I don't know the nuts and bolts of it. 
this suggests it might be doable : 
[http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Local_And_Remote_Forwarding.html](http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Local_And_Remote_Forwarding.html)

---

### Post by ZarathustraDK on 2009-12-15
> **koenn said:**
> This is why I suggested openvpn : it builds a tunnel at network (IP) level, so it's trivial to set up routes through that tunnel and allow other PC's on a connected LAN to use it. Pretty standard network administration.

Problem is that our users are scattered around a lot of different locations, and they move around a lot between different locations with their boxes. Yeah, we could have a dedicated box per location, but that would be a lot of boxes to administrate, each with their own local peculiarities.

> **koenn said:**
> with ssh tunnels, your one lever higher up, at TCP-level, so routing doesn't work there.
You can probably work around it by setting up additional ssh tunnels to connect to the forwarded port on the server, from other PC's on your LAN - maybe something with "local" and "remote" tunnels

Yeah it's something along those lines I'm after, making the server somewhat like a hub of outbound connection-hooks that the users can reverse-ssh to, while the supporters can latch on to any of those connections with vnc when it's made. The first part works, now we need to figure out letting the supporter access the user-connection waiting for him at the server.

> **koenn said:**
> Never done that, so I don't know the nuts and bolts of it. 
this suggests it might be doable : 
[http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Local_And_Remote_Forwarding.html](http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Local_And_Remote_Forwarding.html)

I'll have a look at it, thanks ;)

---

### Post by dmizer on 2009-12-15
Yup, VPN is the way to go.

Configure one VPN server and one router. Let all the other machines connect to the server as needed.

This will require a VPN account and VPN secrets for each guest, but with something like [ebox](http://www.ebox-platform.com/) as your VPN server you'll be able to set up the VPN server and create VPN accounts with a slick web interface.

Once you have this set up, then both your support staff and your users can be anywhere in the world. Both the support staff and the users can log into the VPN server, connect to eachother, do what's needed and log off.

Cautions:
Learn to use the CLI for fixing problems. VNC or any remote desktop option is usually unusably slow over the WAN even with compression and bandwidth limiting options. Your ability to have a usable desktop on the remote machine will depend on both the speed of your VPN server's internet connection as well as the speed of the guest's internet connection.

My experience has been that remote desktop has been barely usable even over a LAN.

---

