---
title: "Print Server Syntax In Between Two Routers"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by chiques on 2009-10-04
Hello Linux Community,

I currently have a home network that looks something like:

::::Ethernet Router:::Wireless Router/Modem::::Internet::
----------::-------------------::----------------------- 
   Print Server-----------Wireless Access--------------


If I'm connected to my ethernet router, I can configure my print server on ubuntu using **Idp://192.167.0.1/printer**. My Wireless Router/Modem has an IP of 192.168.0.1.

I want to print from the Wireless access bridging through the Ethernet Router but I can't seem to get a connection. I tried:

**Idp://192.168.0.1/192.167.0.1/printer** but was unable to connect to my print server. 

Am I using the correct syntax? If I am, then is the problem most likely in my router configuration?

P.S. I am able to access shared folders on my other Linux workstations connected to the ethernet router.


Thank you for any help.

---

### Post by ermeyers on 2009-10-04
Problem #1:  We need to get rid of the 192.167.0.1 address, so we need to change it to 192.168.N.M something. We'll see.  Your diagram makes very little sense to me.

Your Wireless Router/Modem has an IP of 192.168.0.1 .
Your Ethernet Router has an IP of ? .

The **Idp://192.168.0.1/192.167.0.1/printer **syntax is way off.

Given that your wireless router is network 192.168.0.0.

What is your ethernet router's IP?

---

### Post by chiques on 2009-10-05
> **ermeyers said:**
> Problem #1:  We need to get rid of the 192.167.0.1 address, so we need to change it to 192.168.N.M something. We'll see.  Your diagram makes very little sense to me.


-Sorry about the crappy diagram. I have also corrected the IP addresses to what I'm actually using. I've attached a different diagram (please see). From what I gather here, I need to make sure my IP's are all 192.16**8.1**.XXX.

What is really confusing is the fact that I have 192.168.1.1 and 192.169.1.1 and I can connect to both routers when using the ethernet router but not the wireless router. 

> Your Wireless Router/Modem has an IP of 192.168.0.1 .
Your Ethernet Router has an IP of ? .


Wireless Modem Router- 192.168.1.1
Ethernet Router - 192.169.1.1

The reason I changed these IP's so much was because the DHCP would assign my ethernet router the IP 192.168.1.1 (which is my modem IP) and had me going nuts because it would hose my network.

> The **Idp://192.168.0.1/192.167.0.1/printer **syntax is way off.

-OK, so this is wrong.

Given that your wireless router is network 192.168.0.0.

> What is your ethernet router's IP?

-192.169.1.1

I appreciate your help.

---

### Post by ermeyers on 2009-10-05
Use networks (subnets) 192.168.0.0 and 192.168.1.0, etc.
 
 Looking from your wireless modem/router, you're trying to use 192.169.1.1 to go "inside" to your ethernet router, but it actually goes "outside", so that's why you can't address your ethernet router.  The 192.169.1.1 address needs to go, because it's not a private address.  See [http://en.wikipedia.org/wiki/Private_network#Reserved_private_IPv4_address_space](http://en.wikipedia.org/wiki/Private_network#Reserved_private_IPv4_address_space) and [http://en.wikipedia.org/wiki/Subnetwork](http://en.wikipedia.org/wiki/Subnetwork) for background.

> The reason I changed these IP's so much was because the DHCP would assign my ethernet router the IP 192.168.1.1 (which is my modem IP) and had me going nuts because it would hose my network.
 
Between your wireless modem/router and your ethernet router, use network 192.168.1.0.
Wireless router = 192.168.1.1
 Ethernet router = 192.168.1.2
 
Between you ethernet router and your printer, use subnet 192.168.0.0.
Ethernet router = 192.168.0.1
Printer = 192.168.0.2

---

### Post by chiques on 2009-10-05
That clears up much confusion. Thank you for the detailed response.

---

