---
title: "Can anyone explain how to ssh through a firewall?"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by EQvan on 2009-09-13
Hi... 

My office has a small 10.x.x.x subnet behind an IPcop firewall.  I have full access to everything, including the firewall, when I'm at work but I'd really like to be able to SSH through the firewall and log on to any of the machines on the office subnet from home.

I thought a VPN would give me this capability, so I got onto the firewall, installed Zerina, and set up a VPN.  I generated a certificate, installed OpenVPN on my (Vista) laptop, and as far as I can tell, everything works!  I get a little OpenVPN GUI icon, and it says I'm assigned to 10.0.100.6.  But... what does that mean?

I expected the VPN to give me a whole new subnet, so that if there was machine on my office subnet with the IP address 10.0.0.43, the VPN would map some address like 10.0.100.43, so that I could SSH to that machine.  What does the single 10.0.100.6 mapping mean?  There's more than one machine on that subnet, and although I can PING 10.0.100.6, I can't SSH to it, FTP to it, HTTP to it, etc.

I've scoured the Internet (and this site) and there are a number of questions and answers on this subject... but they use lots of networking terminology that I don't understand.  I don't really care about VPNs as such, all I want is some way to get an SSH login to the machines on my office network.  Can anyone undertake to explain how to do this?  Very humble thanks...

---

### Post by mrbiggbrain on 2009-09-13
Most likely you will need to open the ports, and then forward them to the correct PC. If those ports are commonly used, Set up another port to use for your own uses, configure your SSH server to work on that port, then open and forward the new ports.

---

### Post by kevdog on 2009-09-13
You either need to configure the firewall to forward the ssh ip request to the ssh daemon running on a specific IP address behind the firewall (basically configure port forwarding), or you could do the proverbial reverse ssh tunneling which would not require you to configure your work's firewall if it allows outgoing ports.

---

### Post by gombadi on 2009-09-13
People - The OP has installed a VPN. This means that he is bypassing the firewall and therefore does not need to configure the router to forward port 22 to any internal machine.

> 
I expected the VPN to give me a whole new subnet, so that if there was machine on my office subnet with the IP address 10.0.0.43, the VPN would map some address like 10.0.100.43, so that I could SSH to that machine. What does the single 10.0.100.6 mapping mean? There's more than one machine on that subnet, and although I can PING 10.0.100.6, I can't SSH to it, FTP to it, HTTP to it, etc.



EQvan - You need to setup routing on your home machine and configure OpenVPN to send packets for the office subnet via the VPN. A VPN will not map every IP address on a remote subnet to an IP address on the VPN subnet.

On your home machine you configure it to send packets for the 10.0.0.0/24 network via the VPN. As the VPN is running on the router/firewall in the office it will pickup packets heading to 10.0.100.6 and direct them down the VPN to your home machine.

---

