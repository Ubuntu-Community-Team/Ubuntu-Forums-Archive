---
title: "Share internet connection"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by dolphin194 on 2012-05-24
I have a Dell PowerEdge 2650 running Ubuntu Server 10.04, and I would like to share the internet connection on it to another router.

Now here's how i want my network map to look like
**Internet >> Modem+Router >> Server >> Router**


The Router is connected to the server computer's 2nd Ethernet port

In Windows, doing this is as easy as highlighting the connections and creating a Network Bridge, but I want to do this in Ubuntu Server.

Is this possible?

---

### Post by DELL JonathanS on 2012-05-24
[FONT=Calibri]To create an Ethernet bridge joining two LAN segments, see [https://help.ubuntu.com/10.04/serverguide/network-configuration.html#bridging](https://help.ubuntu.com/10.04/serverguide/network-configuration.html#bridging). Since you are connecting two interfaces via bridge (presumably eth0 and eth1) you'll want to make a modification to that recommended configuration -- add "eth1" to the end of the "bridge_ports" line, so it reads "bridge_ports eth0 eth1".[/FONT]
[FONT=Calibri] [/FONT]
[FONT=Calibri]If instead you want the 2650 to function as a gateway/router for one ore more hosts behind the router you're sharing with (like XP's Internet Connection Sharing) you'll need to manually assign a static IP address, configure network address translation in the firewall, and enable kernel packet forwarding. These steps are described at [https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29).[/FONT]
[FONT=Calibri] [/FONT]
[FONT=Calibri]The 2650 is a decent old machine quite up to the task you have planned for it (disclaimer: I work for Dell!), and Linux's robust and stable network stack is well-equipped to handle bridging/routing. Let us know if you run into any trouble with the steps and we'll try to help out.[/FONT]

---

