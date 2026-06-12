---
title: "OpenSSH Configuration Help"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by jgomez2 on 2012-12-05
Hi Community,

I have recently been trying to set up the ability to ssh into my home computer. I followed instructions here:

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

and here:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

To make it so my computer listens for specific ports, and only allows access with an RSA key. However, when I try to log into my computer while on another network it does not let me. It says 'Connection timed out'.

It wasnt all that surprising to me since I bet a million people have the IP address that comes standard with most routers of 192.168.X.Y , so my client computer might have a hard time finding my desktop. A buddy of mine told me to use:

ipecho.net 

to find my 'real' IP address. When I tried the IP address I found there, it simply said, connection refused. I even tried 

```

ssh -p MySpecificPort username@MyRealIP  

```

and it did not work. I tried this from the same laptop which generated the RSA key. 

Does anyone have any ideas?

[I]info:

Client: Ubuntu 12.04 HP Mini110 
Host: Ubuntu 12.10 HP Pavillion HPE


[/I]

---

### Post by wayover13 on 2012-12-05
If I'm understanding you correctly, it sounds like your computer is on a private LAN. If so, no computer outside that LAN is going to be able to ssh into it unless you have a gateway/router that does port forwarding. The ipecho thing you were told about, when run from said computer, tells the address of the gateway/router the computer sits behind. But unless the gateway/router has ssh running on the port specified, or unless it can be set to forward that port to the same port on the computer you're trying to ssh into, it's not gonna work. I'd say check your gateway/router and see if you can and set up port forwarding on it.

James

PS By the way, I also use a non-standard port for ssh'ing into my computers, but the non-standard port is the one the router leaves open on the internet side, while the port to which it forwards on my computer inside the private LAN is the standard ssh port (22).

---

### Post by jgomez2 on 2012-12-06
If by private LAN you mean my crappy ISP gives me a modem, I hook it up to a router to provide WIFI to my apartment then yes, I am on a private network. 

So I can set up my router if you look at the attached screen shot, but im not quite sure what to do, despite your instructions ... sorry

---

### Post by drmrgd on 2012-12-06
You have to think about it like this.  The IP address that the ISP gives you (which is what the outside world can see) is actually assigned to the router in this case.  Then the router assigns new IP addresses to each interface that's connected to it.  

What you'll need to do is to set up the port forwarding in your router to send traffic that's coming to your router's IP address to the IP address and port you have OpenSSH listening on.  So, in the screen you posted, click add Custom Service (Netgear does not have a SSH option in the drop down menu for some reason...at least it's not on mine), and name the service what you like (I think SSH would be ideal).  Then enter the IP address of the computer that's running OpenSSH (192.168.1.x) choose the custom port you have OpenSSH listening on, and save.  Now when you SSH to your public IP address (the one the ISP gave your router), the router will direct that traffic appropriately. 

Hope that helps!

EDIT: one other thing I forgot to mention that's not intuitive.  The starting port and ending port will be the same (the custom SSH port you've chosen).  The port range they offer is for gaming servers where you need a port range instead of a static port.

---

### Post by jgomez2 on 2012-12-06
Thanks for the help, that worked.

---

