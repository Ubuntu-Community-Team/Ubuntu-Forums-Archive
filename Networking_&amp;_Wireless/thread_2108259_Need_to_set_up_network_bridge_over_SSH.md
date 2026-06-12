---
title: "Need to set up network bridge over SSH"
date: 2013-01-24
forum: Networking &amp; Wireless
---

### Post by batboio on 2013-01-24
Hello! I've searched for solid information on setting up a network bridge for quite some time and while there are many examples on the internet I couldn't find 2 which were consistent with each other :) They all probably accomplish the same thing though...

So here it goes:
I need to set up a network bridge for OpenVPN but I am connecting  over ssh so I need to do this without losing web connectivity on the  server. I am using Ubuntu 12.04 LTS. I know the basics but I am asking  for an almost step-by-step guide so that I don't screw something up and lose my  ssh connection.  
  I've done it while my network manager was still installed and I  didn't lose ssh but I couldn't load web pages from the server anymore. So  either the network manager was helping me (or hindering) or I've done  something wrong. Right now I managed to remove the network manager and  edited /etc/network/interfaces so I have internet, but I don't want to do more until I have some answers.


Right now my /etc/network/interfaces looks like this:


auto lo
iface lo inet loopback

auto eth0
allow-hotplug eth0
iface eth0 inet dhcp

---

