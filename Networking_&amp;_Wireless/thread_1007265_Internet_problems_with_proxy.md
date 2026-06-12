---
title: "Internet problems with proxy"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by shum123 on 2008-12-10
Hey.
Internet connects using an ethernet through a proxy. Set up according to instructions ie. using network proxy, but network manager doesn't connect to a network.

The proxy is a university Internet connection. It does support Linux but doesn't offer information for setting it up. for getting it to work on xp there are quite a few steps 

[http://www.uclan.ac.uk/information/services/iss/services/files/setup_instructions_for_windows_xp.pdf](http://www.uclan.ac.uk/information/services/iss/services/files/setup_instructions_for_windows_xp.pdf). 

I have it working on XP

Any ideas how I would go about connecting

I'm currently running Ubuntu 8.10 off a live-cd. looking to install after can work Internet

System is Dell Inspiron 1300
Intel Pentium M 1.7GHz. 
512ram  
Broadcom 440x 10/100 Integrated controller

---

### Post by jrasmussen0 on 2008-12-10
Have you gotten the network to work?  It looks like you will have to follow these instructions to get your computer authenticated on the network.  (There may be an easier way using the System --> Preferences --> Network Configuration but I'm not sure)

[https://help.ubuntu.com/community/Network802.1xAuthentication](https://help.ubuntu.com/community/Network802.1xAuthentication)

Once authenticated on the network, you should be able to easily add the proxy configuration to System --> Preferences --> Network Proxy.

Let us know how it works out.

---

### Post by shum123 on 2008-12-10
I think the network is connected, it tries to connect but says it can't get an ip from the connection, so I guess the proxy needs to be set up for that. it does sound like it will work. However I have a Equifax Secure Certificate Authority. the config it shows uses no certificates, any idea how I would implement this?

---

### Post by shum123 on 2008-12-10
Hey.
Turns out the server uses an older version of 802.1x and the network manager was trying to use a new version. All works now. Thanks for the help.

---

