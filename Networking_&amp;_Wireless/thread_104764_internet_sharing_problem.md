---
title: "internet sharing problem"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by gringocl on 2005-12-16
I just downloaded Kubuntu breezy 5.10 last night and installed it on a box at work, trying to setup an internet gateway/router/firewall at work.  We have an interesting setup I am using an verizon wireless PC5740 as for my PPP connection to the internet (were out in the sticks) and eth0 is connected to a linksys WRT54G configured as a wireless AP connecting to 4 windows PCs.  After struggling with getting the evdo card configured and installed and actually connected to the internet!!!! (Yea), I installed DHCP server and have everything locally working.  My problem right now is that I only can access the internet on the linux box and cannot share it accross the network.  I'm sure that there is probably a very simple and easy solution to this but, being new to linux dont really know where and how to solve this.  Please let me know what config files I need to show the output of or what information is needed.  Thank you very much for your time.

gringocl

---

### Post by Lambert on 2005-12-16
On the linux box you need to turn on ip forwarding

change your /etc/sysct..conf file

Before:

# Disables packet forwarding 
net.ipv4.ip_forward=0

 
After:

# Enables packet forwarding 
net.ipv4.ip_forward=1

Not sure if this is the answer as I wasn't 100% clear on your lay out.

if you could draw out your set up a little clearer something like this.

internet - router - linuxbox - 4 windows boxes

---

### Post by gringocl on 2005-12-16
Lambert sorry for not being so clear

Its Internet --- Linux Box --- Wireless Ap --- Windows Boxes.

I'll try to enable the IP forwading, thanks

gringocl

---

### Post by Lambert on 2005-12-16
You may want to also try to run a tracepath command to see where the route stops.


tracepath [www.google.com](www.google.com)

---

