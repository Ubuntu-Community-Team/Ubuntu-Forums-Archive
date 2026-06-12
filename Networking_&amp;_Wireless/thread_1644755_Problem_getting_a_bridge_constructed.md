---
title: "Problem getting a bridge constructed"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by bdemers on 2010-12-13
My first, followed a couple of Ubuntu how tos and used LinuxFoundation bridge doc.  I still have managed to mess it up!

Here's the simple test network,  First -- ALL hardware is fine, I have verified everything, to the last cable.  In fact this is being written from the test network without the bridge running.

OK, I have a firewall that has dhcp server on board, I have a client workstation with dhcp enabled network card(eth1) (the one I current typing from).   There are 2 switches between the firewall and the workstation (eliminate xover issues when testing) That's it.  All is well.  Now I want to place a computer in line between the firewall and the workstation.  It is a 10.04 server install, no gui, minimal install.  It has 3 network cards, One of these ports was used to set up the server.  It is set up dhcp and it works just fine, I spent all kinds of time ssh'ing into the box, so the dhcp client is good to go.

I disconnected the cable to that interface and ran a cable from the firewall's switch to one free port(eth0) and a cable from the workstation switch to the other free port(eth2).

From the console I do ifconfig -a and there are all 3 eth's, 0,1, and 2

I then open /etc/network/interfaces and to lo and eth1 I add this:

auto br0
iface br0 inet dhcp
	  pre-up ifconfig eth0 0.0.0.0 down
	  pre-up ifconfig eth2 0.0.0.0 down
	  pre-up brctl addbr br0
	  pre-up brctl addif eth0
	  pre-up brctl addif eth2
	  pre-up ifconfig eth0 0.0.0.0 promisc up
	  pre-up ifconfig eth2 0.0.0.0 promisc up
	  post-down ifconfig eth0 down
	  post-down ifconfig eth2 down
	  post-down brctl delif br0 eth0
	  post-down brctl delif br0 eth2

close and restart the box.

after logging in again I do an ifconfig br0.

It shows up, but without an ipv4 address

I then do brctl and the bridge br0 is defined with an id#, no stp but....no interfaces either.


So, I've messed up somewhere, but I'm too new at this to troubleshoot more than what I've just explained.

I'd appreciate some guidance.  Heckling is ok, but only if you solve my issue first!

---

### Post by bdemers on 2010-12-13
Here's my /etc/network/interfaces  It doesn't work

auto br0
iface br0 inet dhcp
pre-up ifconfig eth0  down
pre-up ifconfig eth2  down
pre-up brctl addbr br0
pre-up brctl setfd br0 0
pre-up brctl addif eth0
pre-up brctl addif eth2
pre-up ifconfig eth0  up
pre-up ifconfig eth2  up
pre-up dhclient -r br0
pre-up dhclient br0
#post-down ifconfig eth0 down
#post-down ifconfig eth2 down
#post-down brctl delif br0 eth0
#post-down brctl delif br0 eth2


Heres a series of cli inputs, this works

sudo ifconfig eth0 down
sudo ifconfig eth2 down
sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 eth2
sudo ifconfig eth0 up
sudo ifconfig eth2 up
sudo dhclient br0

By works I mean that an ipv4 address is assigned to br0 and I can send data through the bridge

With the interfaces file, no address is assigned to br0 because the interfaces are not attached to the bridge for some reason
I can't send data

I added the dhclient lines to the interfaces file in off chance that it would work--didn't
The rem'd staements were added only for testing, they need to be removed, but doesn't affect outcome.

Any clues how to fix this so my bridge comes up on boot, and releases dhcp on shutdown?

---

