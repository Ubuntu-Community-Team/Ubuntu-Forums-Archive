---
title: "Can't log onto my schools vpn"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by tentel on 2009-04-30
In order to get online at my college, I have to get onto their wireless network, which is local only, and from there I have to get onto a VPN in order to access the Internet.


Using Jaunty 9.04, I simply cannot get this to work.

Here are my schools directions for using the VPN with linux:

[http://www.umassd.edu/cits/wireless/](http://www.umassd.edu/cits/wireless/)

scroll down a little bit to "VPN setup and your notebook"

right below that is a link to a pdf that lists the steps to take.



It tells me to use VPN Connection Manger (PPP Generic), but I can't find it in Add/Remove programs

I found another vpn manager, but it won't connect to the vpn.


Any suggestions would be much appreciated.

Thanks
-Tim

---

### Post by Hobgoblin on 2009-04-30
> **tentel said:**
> 
right below that is a link to a pdf that lists the steps to take.



It tells me to use VPN Connection Manger (PPP Generic), but I can't find it in Add/Remove programs


Did you try just clicking the network manager icon as per those instructions, VPN is there on mine though I still have 8.10

---

### Post by Young Burnsy on 2009-05-01
> **Hobgoblin said:**
> Did you try just clicking the network manager icon as per those instructions, VPN is there on mine though I still have 8.10

The pptn setup is different in the newer version. The OP an I are friends and go to the school and there for are having the same problem.

I just installed Easy Peasy 1.1 on my eee 900 and I have tried to use the 'built-in' version of the pptn vpn setup. Which does not work since there is no 'refuse EAP' option which is required by our VPN. See here (PDF link) [http://www.umassd.edu/cits/wireless/vpn_linux.pdf]("http://www.umassd.edu/cits/wireless/vpn_linux.pdf")
Every time I attempt to connect to the VPN using this pptn the server refuses to make a connection.

So I decide to try Kvpnc even though Easy Peasy is a Gnome interface. Now Kvpnc will connect to the VPN fine and authenticates as it should, how ever the web browser (Firefox 3) functions as if the VPN is not connected. Meaning it still redirects me to the default 'How to connect to the VPN' site.
I spent a while trying to figure this out today to no avail an asked a friend who is a redhat/fedora user and he had no suggestions except to try a different pptn client?(not sure if I am using the right terminology here)

So I'm stuck. Any suggestions?

---

### Post by Qwerty_ on 2009-05-01
I cant connect the VPN at my uni either. When I try to add a VPN from the icon in the top right hand corner. The button to add a VPN from the VPN section is greyed out and I cannot click it.

---

### Post by Young Burnsy on 2009-05-01
> **Qwerty_ said:**
> I cant connect the VPN at my uni either. When I try to add a VPN from the icon in the top right hand corner. The button to add a VPN from the VPN section is greyed out and I cannot click it.

You need to add a pptn client from the synaptic manager.

---

### Post by Qwerty_ on 2009-05-05
Thanks Burnsy ill test it out.

---

