---
title: "Using two different LAN connections at the same time"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by morningstar.fallen on 2012-12-04
Hi everyone,

I am trying to set up a very specific ubuntu box at work. The idea is as follows:

It would be connected (via wired eth) to two lines. One of them is our firewalled domain network and the other one is a separate broadband connection from a different ISP.

The goal would be to run two virtualbox vm's: 

First one would be a domain XP machine sharing a USB printer with the rest of our Active Directory. Ideally this one would use the company LAN.

The second one would be a non-domain XP machine acting as a remote desktop server for our users to connect to and surf in the unfiltered internets. This one would only connect to the broadband line. This would be the standard (over-the-internet) RDS with the broadband router forwarding the port 3389 to the right machine.

Now I do have a decent idea how to set the vm's up, but I don't know how to make the underlying ubuntu machine to handle the two separate lines.

Any suggestions are welcome!

---

### Post by SeijiSensei on 2012-12-04
1) Configure the two adapters with [static addressing]("https://help.ubuntu.com/12.04/ubuntu-help/net-fixed-ip-address.html") in /etc/network/interfaces. The link describes how to do with the GUI Network Manager.  If you'd prefer, you can edit the interfaces file directly as [described here]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing").

2) Install the two VM instances.  I use VirtualBox which is pretty much a no-brainer to install. If you choose "bridged mode" you can bind a virtual adapter in each guest to a specific adapter on the host.  Then configure each guest's IP addressing accordingly.

VirtualBox offers a variety of networking schemes.  [Read this](http://www.virtualbox.org/manual/ch06.html) for more details.

If you decide to install VirtualBox, I recommend following the instructions for "Debian-based" distributions [here]("https://www.virtualbox.org/wiki/Linux_Downloads").  If you add the official repository to your system, the OS will handle any required updates to the VirtualBox application like it does for all other applications in the standard repositories.

---

### Post by morningstar.fallen on 2012-12-10
You sir are a hero! :) Everything worked nicely and smoothly, thanks a lot!

---

