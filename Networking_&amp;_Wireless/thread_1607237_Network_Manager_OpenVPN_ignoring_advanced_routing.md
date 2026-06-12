---
title: "Network Manager OpenVPN ignoring advanced routing"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by ryanczak on 2010-10-27
I am trying to get the network manager openvpn plugin to ignore the routes pushed to the client by the openvpn server and defin my own. 

Checking the Ignore automatically obtained routes checkbox does not seem to do anything. Using the command line version you can specify the route-noexec option which works great. 

Also, Is there a way to pass variables to the route commands so that I can define the gateway of my custom routes as one of the arguments passed by openvpn on connect? I do this using the command line version of openvpn by using $4 in my up scripts. 

Anyone have any insight? Would be nice to use the GUI tool but this lack of functionality makes that difficult for me.

---

