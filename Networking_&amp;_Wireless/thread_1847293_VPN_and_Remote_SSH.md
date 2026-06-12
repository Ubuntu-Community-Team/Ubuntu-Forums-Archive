---
title: "VPN and Remote SSH"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by mbaker2311 on 2011-09-20
[COLOR=#0000ff]Is there an appliance out there that support Linux/Ubuntu servers? In other words, is there a client I can install on a Linux server that will allow it to establish a VPN connection to my office?  I know I can run OpenVPN, but I am looking for an appliance (SonicWALL, Barracuda, Cisco) that will allow me to establish VPN connections to remote office servers.  Have YOU ever worked with such a device?[/COLOR]

---

### Post by Dangertux on 2011-09-20
As far as I'm aware the Sonicwall client will not connect to anything but a Sonicwall VPN. That being said I don't believe they even have a Linux client. If the remote service is a barracuda device you should be able to access Barracuda's secure VPN via SSL through a web browser, regardless of OS.

As a point of clarification your initial post was a little indescript in what you are looking for. Are you looking for a client to connect to an EXISTING VPN? Or, are you creating a new VPN? If you are creating a new VPN in your office be aware that any of the solutions will be compatible with Linux so long as the proper configuration is present. However, not all solutions offer a Linux compatible client. I would suggest using either Cisco or Barracuda if you're looking to add to your office network and have the most compatibility possible. 

If you're only looking from the client perspective I would suggest OpenVPN , since it's compatible with most major VPN's (you will still need information from the remote side)

---

### Post by mbaker2311 on 2011-09-21
What I'm trying to do is move away from OpenVPN to an appliance.  I would need something that I can load on an ubuntu server, say in Alabama, that would connect to this appliance (also, it would have to auto-connect as there is no one at the sever to launch anything.)  Let's say the appliance is in New York.  Once it is connected, I have a VPN tunnel to this ubuntu box.  Then, say someone in Ohio needs to connect to this ubuntu box via SSH or TELNET.  They would launch their own client connection to the appliance (they are running Windows and Mac OSes.)  Now, they have a VPN to the appliance and an IP, the server has a VPN to the appliance and an IP, so the person in Ohio should be able to connect over SSH and TELNET to the server in Alabama.

---

