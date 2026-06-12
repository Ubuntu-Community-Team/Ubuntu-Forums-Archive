---
title: "network manager vpn (openvpn) problems"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by sarikan on 2009-07-18
Hi, 
When I create a vpn connection in network manager either using entering values by hand or by importing my existing openvpn client config file, syslog does not contain some of the statements related to selected cipher. 
If I start openvpn from a terminal, I can see that the used encryption algorithm, blowfish is printed out, but when I take a look at syslog, network manager output does not contain this section. It makes me nervous, since I want to see the used encryption. 

Also, if I start openvpn from network manager, the dns address is pushed by the vpn server, which is the right way things should work,but If I start it from the command prompt with sudo openvpn myconfig.ovpn the dns server pushed by the vpn server is not received. 

So how can I get a more verbose output from vpn via network manager (tried gconf to add paramater verb, but no change) ? 
And why openvpn invocation works right from network manager applet and does not work exactly right from terminal? 

Any help about these issues would be appreciated a lot

Best Regards
Seref Arikan

---

