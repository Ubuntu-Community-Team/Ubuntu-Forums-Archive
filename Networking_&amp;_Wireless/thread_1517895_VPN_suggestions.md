---
title: "VPN suggestions"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by Styles on 2010-06-25
Ok this is all I need simple VPN with authentication to external Radius server.

Here is what I have done to try and get this goal accomplished.

1st try using PPTPD and Radius plugin

No matter what I have tried (long explanation here [http://ubuntuforums.org/showthread.php?t=1517219](http://ubuntuforums.org/showthread.php?t=1517219) ) I can't get PPTPD to talk to my Radius server, even though I can authenticate using the same server and radius server using pam radius. PPTPD just won't, and so far the POTOP mail list has been quiet since my post to them and no replies/ideas in my other post, see forum link above.

2nd try using OpenVPN and their pam auth plugin. 

I give up on this one! I have the server working great BUT! As soon as I enable the plugin /usr/lib/openvpn/openvpn-auth-pam.so in the config I get this when trying to start the VPN server. kernel: [3725586.167177] openvpn[28364]: segfault at 0 ip 00007fd6e5e38fb4 sp 00007fff434f18f0 error 4 in openvpn-auth-pam.so[7fd6e5e38000+3000] 

Google turns up nothing on Segfaults on the openvpn-auth-pam.so

Ugggggg at my wits end, anybody have any other suggestions? I'm at a total loss ATM.:confused:

Thanks for your time,
Eric

---

### Post by jonobr on 2010-06-25
Forgive my ignorance and I may not be able to help, but Im trying to understand whats happening.
Are you setting up a PPTP connection and tunneling your radius authentication packets to your radius server?
Or are you setting up the tunnel after the user has been authenticated to Radius?

If its the second case then Im wondering if  posting the results of the original authentication attempt from the ubuntu side may help?

Assuming that your using port 1545 
tcpdump -w authentication.pcap -i any -s 1600 port 1545

or if your using port 1812 
 tcpdump -w authentication.pcap -i any -s 1600 port 1545

This may show the request going out and if there is some answer.
Again forgive me if this is way offbase

---

