---
title: "Ubuntu, AD, and EAP-TLS"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by de Silentio on 2010-02-11
I have what I think to be a complicated setup and need some direction. As a disclaimer, I'm new to Ubuntu and pretty new to Linux. I don't know that much, but can figure a lot of stuff out.
 
We purchased some netbooks (Dell 2100n) and we are running Ubuntu Netbook Remix 9.somthing on them. I have the wireless working and can connect to our guest network with no problem (read: wireless is working).
 
I cannot, however, figure out the best way to configure the netbooks to do what I want them to do. Here is some background info on the way my wireless network is configured. We have two SSID's setup that serve different functions. One is a guest wlan that has open access, the other is a secured wlan that requires a certificate for authentication. This can be either a User or Computer certificate. The CA is a Windows 2003 R2 machine and the certs are validated on this machine. The Secured wlan uses RADIUS (IAS on the CA), and the policy is currently that the computer or user has a valid cert provided by the mentioned CA.
 
My Windows machines get a computer certfiicate via Group Policy and through Group Policy are configured to automatically pick the Secured Wlan and use EAP-TLS to authenticate against the RADIUS server. This allows for anybody on the network to pick up a laptop, turn it on (with wireless being on of course) and authenticate against our DC's. Essentially, having a wireless computer works just like a wired computer.
 
On the Ubuntu NBR's, I setup active directory authentication using Likewise AD and this is working when using a wired connection.
 
** So, here is what I want to do with my netbooks. I want any one in the organization to be able to turn on the netbook and log into the domain with the wireless connection (just like the Windows machines described above). 
 
So far, I've discovered that I cannot use PEAP to do this, as you need to log in to the machine first, then to the wlan, so I have to use EAP-TLS (certificate based). I cannot use a user certificate, as the user would have to log into the netbook first then request the certificate. I cannot use GP to push a computer certificate, or at least I don't know how to do this.
 
I guess my first question is how to get a computer cert onto ubuntu, then how do I configure ubuntu to always look at the Secured Wlan and connect automatically before anyone authenticates. Is this possible? Has anyone setup ubuntu this way before?
 
Thanks in advance for your help.
 
John Dombrowski

---

