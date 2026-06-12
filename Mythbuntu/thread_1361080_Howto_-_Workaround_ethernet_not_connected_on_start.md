---
title: "Howto - Workaround ethernet not connected on startup"
date: 2009-12-21
forum: Mythbuntu
---

### Post by djm-uk on 2009-12-21
Not a very good title but here's the scenario...

Myth(buntu)combined backend/frontend set up to serve remote AV clients (EG WMP) so the backend IP addresses in setup are the real addresses of the Interfaces not the 'loopback' 127.0.0.1 address. But if the box starts up when the attached ethernet device (hub/switch) is off it fails because the ethernet interface is down so it can't connect to the backend..

So we need an 'always on' ethernet interface. Played with using a loopback with a 'real' address which didn't work as I couldn't get forwarding of the uPNP broadcast to work. I then set up an ethernet bridge which provides a 'virtual' bridge interface that can be assigned an address and you can then assign one or more 'physical' interfaces to it...

Basic steps (use sudo etc where required)

in theory you should 'down' the ethernet interface before you start setting up the bridge (but not before you have done the apt-get...) and assign them 0.0.0.0 ip addresses.

Get the required package
apt-get bridge-utils

Create a named bridge interface
brctl addbr <bridgename>

Give it the IP address you want the machine to have
ifconfig <bridge> <ipaddress> netmask <subnet>

add the existing interfaces to the bridge
brtcl addif <bridge> <ethX>

test it
ping <ipaddress> 
& unplug the ethernet cable - the ping should carry on responding!

HTH

David

(BTW <something> indicates that you need to provide an appropriate value to replace the <something>)

---

