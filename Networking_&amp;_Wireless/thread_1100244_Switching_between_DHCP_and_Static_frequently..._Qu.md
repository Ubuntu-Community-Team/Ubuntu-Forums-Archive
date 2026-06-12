---
title: "Switching between DHCP and Static frequently... Question."
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-03-19
I have a work laptop I dual boot on. It also just so happens I am experimenting with the very attractive open source cloning software known as FOG.

At work, we use DHCP with a 10.52 style IP scheme.

I'm not the network administrator and I choose to keep FOG (though it being network based) off of the network. I keep FOG on a localized LAN with no external access so I can push images to other computers at my desk through a 24 port Dell gigabit switch I have.

To make things easier, I disabled Network Manager from starting up and decided to edit the interfaces file.

I created two interfaces files and stored them in Documents - DHCPScript + StaticScript. Each script resides in its respective folder.

Then I wrote a script for each, which simply copies the DHCPScript from Documents to /etc/network/interfaces, and after that restarts the network interface, therefore giving me a new IP address from the DHCP server.

I'm testing it here on my LAN. The Static side of it works great and immediately I can access 192.168.1.100 which is the address to my FOG "server" interface to manage images and deployment. When I switch to DHCP, although I pick up an IP address (on my LAN it comes up as 192.168.1.115) I cannot get external access. I can ping internally, but anything externally doesn't work. It's as if my gateway isn't swinging over or something.

I haven't tested this at work, but even running the networking restart command doesn't seem to cure it, no matter how many times I run it. It seems to be random when I can suddenly gain external access. 

The only thing that seems to cure it is rebooting after I set my interface to DHCP.

Is there anything else I can do?

---

### Post by kevdog on 2009-03-19
Please post your script files.  You may have to add setting the gateway or dns server in your script.

---

