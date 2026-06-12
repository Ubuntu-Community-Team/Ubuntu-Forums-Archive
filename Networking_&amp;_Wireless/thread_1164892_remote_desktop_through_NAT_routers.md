---
title: "remote desktop through NAT routers"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by rduke15 on 2009-05-20
I'm looking for a solution to support a remote Ubuntu user. 

Obviously, the problem to solve is the **NAT traversal, without the need to modify the router configuration on either side of the connection.**

To make this possible, **I do have a (Debian) public server which could act as a "forwarder"**, on which I can install and configure whatever is needed.

What can I install on my public server so that we can both connect to that server and I get the remote user's Ubuntu desktop on my screen.

There are web services offering this, but as far as I know, they tend to be Mac/Win only, and also usually not free.

I'm also aware of the nat-traversal script, but that seems to be only for command-line access. I need to see the GUI.

Thanks for any pointers to possible solutions, forwarding programs, instructions...

RD

---

### Post by Peter09 on 2009-05-20
Well I know how to do it by only modifying your NAT router and leaving the client side router alone - is this good enough?

---

### Post by rduke15 on 2009-05-20
> **Peter09 said:**
> is this good enough?

No.

(because I am often in places where it's not my router)

---

### Post by Peter09 on 2009-05-20
I actually am able to do this. I run a virtual machine which allows me remote log in through nxfree. From the virtual machine, which I can see remotely, I can the establish a client desktop - a bit convoluted but it works. 

The virtual machine part is only for security, you could just do it from a server.

---

### Post by rduke15 on 2009-05-20
I do have NX server on the public machine, but I'm afraid I don't see how I could use it as a relay/forwarder between the 2 NATed hosts.

---

### Post by Peter09 on 2009-05-20
The NX server just lets you see the desktop of the server machine. You can the use VNC to see from the server to the client.

---

### Post by little_penguin on 2010-04-25
There is now a linux package (.deb, .rpm or tarball) available for Teamviewer 5, which has been out since mid April 2010. It uses Wine, so it is not exactly linux-native, but it works very well. It works with linux as either the client or the server. There is no need to forward ports on NAT firewalls and it is easy to use. Since mobility and no port forwarding is a must for you, i.e ruling out the usual choices like SSH, NoMachine NX, VNC tunnelled through SSH, etc., this might suit your scenario.

[http://www.teamviewer.com]("http://www.teamviewer.com/")

---

### Post by rduke15 on 2010-05-20
Yes, I tried the new Teamviewer .deb package, and it worked. The supported user had a Windows machine with a huge screen, so it was pretty slow, but it worked.

But I'm still hoping for a solution which wouldn't involve an unknown third party relaying my traffic.

There must be some way using open source tools to do the same kind of forwarding which teamviewer does, but on my own public server instead of theirs.

---

### Post by little_penguin on 2010-05-22
Ok, this is just an idea - to use your own public Debian server for remote support traffic between you and your Ubuntu user from multiple locations (instead of using a hosted service like Teamviewer, Logmein and co.), perhaps you need to go down the VPN route, using your Debian server as a Virtual Private Server (VPS) in a one-to-many configuration?? The following link might help. The principle is similar to what you want to do (except for the stuff about PBX, but that is just one scenario). If not, the article might be part of the solution and hopefully contains some pointers:

[http://blogs.elastix.org/en/2010/03/remote-access-via-openvpn-no-port-forwards-needed-on-client-side/](http://blogs.elastix.org/en/2010/03/remote-access-via-openvpn-no-port-forwards-needed-on-client-side/)

I have not set anything up like this myself, but I am sure there are plenty of experts in these forums who will help you out.

---

