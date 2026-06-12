---
title: "INternet connection sharing in Network manager - no DHCP server"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by jasonbrisbane on 2010-10-14
HI,

How do I tell the shared connection that it has a static IP and that I dont want a DHCP on the network?

Do I have to set up DHCP on the box with the shared connection, even if that box only runs DHCP for a single IP address being the eth0 that is shared?

Or can I tell the shared connection that it has a static IP and still allow network manager to run the shared connection?

Or should I specify static IP's for all clients and the shared network manager and install say firestarter on the gateway to run the NAT for the eth0 out to eth1....


Regards
Jason B

---

### Post by jasonbrisbane on 2010-10-14
bump?

no responses?


Summary:

I have two network connections eth0 (wired) and eth1 (usb modem). 
I want this box to be a gateway and share the eth0 with routing to allow connections on the eth0 lan to go out the eth1 port.
I am using network manager.
When using network manager and SHARE THIS CONNECTION in Ipv4 tab, it (appears to) wants me to have a DHCP server to assign dhcp ip addresses to the eth0 connections.

Question: Do I NEED to set up a DHCP server for this on this machine? If so then why not list this as a requirement in the installed files or dev notes, etc?

Can I set (obviously in text file) a setting to allow a static IP on this port?

How do I get ICS working on static IP's on a LAN?
Do I need to only set a DHCP for the internal port on eth0?

Thanks in advance

---

### Post by joeoshawa on 2010-12-08
I have set this up at my ex's house so i can administer her set-up from here. She has two computers a dsl connection and no gateway. If dhcp is fine for you then great all you need to do is leave dhcp in the little window that's all i did. If you want a static ip then I have some of the same questions as you. What i want to do is this, I want to forward a port for ssh (not 22 but haven't decided on a port yet so for arguments sake say 3456) can i assign a specific address from the computer the dsl modem is connected to using the network manager and then just port forward 3456 to said computer? the problem is the head computer is the firewall as well but i only have and can have access to that computer when i go there. No ssh (I do not want ssh on the firewall only the computer behind it.) I have ssh set up on her computer and i can change the port easy (shout out and thank you to writers of the Ubuntu howtos) I just want to make sure when i forward the port and assign the ip i am doing it right due to the firewall being a in use desktop as well. 

As a side thanks to me and my ex there are now 26 former windows users who are now very happy Ubuntu users. Go Ubuntu once you start you never go back.

---

### Post by jasonbrisbane on 2010-12-08
Hi,

I manually set up each machine on the eth0 with a static IP in the 10.42.43.x range (2-5 actually).

Now with network manager using dhcp and auto setting the routing and firewall rules, I can get all traffic through the router (a Dell Zino HD "media center" box, also hooked to by LCD TV!).

Next step is to set up a transparent proxy and graphical firewall program so that I can see and restrict access to websites and ports for different PC's and users. (including deny anything on a DHCP port!).

This will allow me to protect my kids form the harsh reality of the internet, at least for a few years - hopefully 14-15 years (oldest is 3 ATM).


Looking good!



For your question:

You will have to set up port forwarding on your router to forward bidirectional requests on the ssh port.

If you want to change the SSH port for any reason(eg to 3457) then you will have to change the pc AND the router forwarding...

---

