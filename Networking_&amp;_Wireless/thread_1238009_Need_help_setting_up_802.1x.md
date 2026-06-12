---
title: "Need help setting up 802.1x"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by iankellogg on 2009-08-12
Hi, I have a new laptop with ubuntu 9.04 installed on it. My only real problem I am having with ubuntu is trying to figure out how to setup 802.1x for my school. I have checked around the forums and google and I cant seem to figure it out. The instructions on the schools website is pretty pathetic so they are of no help to me.

Penn State Wireless 2.0 - Get Connected
Generic Setup Instructions
SSID (aka, Network Name): 	  psu    *note that the SSID is case sensitive and must be all lower case
Network Type: 	  Infrastructure
Security: 	  WPA2-Enterprise (not WPA2-PSK)
Encryption: 	  AES
Authentication Type: 	  EAP-TTLS
Authentication Protocol: 	  PAP
Certificate Authority: 	  Thawte Premium Server CA
Authentication Server: 	  radius1.aset.psu.edu
  	 
If allowed by your client program, it is also recommended that you enable options to Validate Server Certificate and Verify Server Name.

 
I really cant figure out which options go where in the network manager. 
If you have a solution that can be done in the network manager or with some terminal commands Im all game. Not afraid of the terminal or vi.

---

### Post by frmdstryr on 2009-10-22
Trying to figure it out too, I think we just need to get the certificate somewhere then use tunneled tls.

---

