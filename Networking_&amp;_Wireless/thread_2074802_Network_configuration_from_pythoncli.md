---
title: "Network configuration from python/cli"
date: 2012-10-22
forum: Networking &amp; Wireless
---

### Post by sdenton4 on 2012-10-22
Hello!

I have a bunch of computers (40), and a dictionary for associating each mac address to an ip address.  The machines are cloned disk images.  I'm writing a python script that should run exactly once on each machine (after being re-imaged) to give it the correct IP address to match the MAC address of the ethernet card.

I tried just directly manipulating the files in
/etc/NetworkManager/system-connections
but after doing so the connection doesn't show up in the network manager.  I've copied the file structure of a working connection exactly, so I'm unsure why it's not showing up.  Does one need to access the config files through another service, instead?

---

### Post by steeldriver on 2012-10-22
I don't know if it's supposed to work that way - did you generate a new uuid for the connection or just copy that as well? 

Otherwise you might want to take a look at the nmcli tool (nmcli con up ... ?) - or a bit of googling throws up this (python direct to the dbus interface)

[http://cgit.freedesktop.org/NetworkManager/NetworkManager/tree/examples/python](http://cgit.freedesktop.org/NetworkManager/NetworkManager/tree/examples/python)

(I'm just guessing - I've never done it)

---

