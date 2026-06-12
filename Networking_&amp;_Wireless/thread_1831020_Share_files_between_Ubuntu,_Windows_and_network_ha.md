---
title: "Share files between Ubuntu, Windows and network hard drive."
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by jwsheff on 2011-08-22
I have solved my problem but not after many hours of reading so many threads on this subject, trying all of the suggestions and spending a lot of time learning what is right and what is not.  I am currently using Ubuntu 11.04 (natty) which after upgrading to, was not able to see my Windows PC or network hard drive from the Ubuntu file browser.  Also could not perform any scheduled backup.
 
 My most important requirement is that I want to use NetBIOS names to access shared resources and not IP addresses.  Many of the threads I followed kept wanting to take me down the path of installing and configuring WINS and Winbind.  That is not the answer because you need to have static IP assignments for each machine and not use DHCP for automatic assignment.  I want DHCP simply so I can add a machine/device to the local network, wireless or otherwise and be up and running.
 

 I am sure we all know we need SAMBA and there are tons of threads to show you how to get and install SAMBA, so I am not spending any time there.  However, the smb.conf was part of the problem which I will explain below.  First let me describe my local network configuration and setup because that was the other part of the problem.  
 
 I use DSL as my broadband connection, which of course requires a MODEM.  I purchased the MODEM before I could get a self contained MODEM/wireless router, so I have a Linksys wireless router behind the DSL MODEM with all machines/devices connected to the Linksys.  When I installed this hardware, I accepted, for the most part, all of the defaults. As a result, the MODEM was not setup with a routing table or a protocol to discover routes.  The Linksys wireless router was setup as a gateway and as such was not creating a routing table.
 
 The first fix was to establish the MODEM as a router and to turn on RIP which in my case was version 2.  I believe that prior to establishing the router table, requests from my Ubuntu machine to discover an IP address using a NetBIOS name was sent to the gateway (wireless router) which passed it to the MODEM and with out a routing table, passed it to the Internet (WAN).  Of course there is no Domain Name Service out on the Internet that will know my NetBIOS name, so it would return an invalid request.  Solving the hardware configuration would tend to make you think that would have been the total resolution, but no.  I was now able to to see my local area network from my Ubuntu file browser, but it was  agonizingly slow and when I would try to open a shared folder it would take forever.  My backup would fail most of the time because it would time out before the discovery was complete.

 The final fix was the smb.conf file.  I used Wireshark to monitor the traffic on my Ethernet port (eth0) and realized that during the discovery process SAMBA was sending out both NBNS inquiries and DNS  inquiries.  The DNS inquiries were going to the Internet and it seemed that SAMBA would wait for a response to both inquiries regardless of the fact it received the local response (NBNS) first.  After a very long time SAMBA accepted the local NBNS response and would display or request the share volume information.  To resolve this problem I edited the smb.conf file with SWAT as I will describe below.  I used SWAT just because I installed it as part of the trouble shooting process, but you could use VI or GEDIT.  Here is what I did to smb.conf:
 
[LIST=1]
[*]Make sure WINS is disabled, I set     it to NO.  SWAT removed the line in the config file altogether.
[*]Set &#8220;name resolve order&#8221; equal     to &#8220;bcast&#8221; by itself, nothing else.
[/LIST]
 Now when I watch the traffic on eth0, the only broadcast is NBNS which will not be routed to the Internet by my MODEM routing table but instead returned to the Linksys which in turn will broadcast to all ports (wired and wireless).  The particular hardware for that NetBIOS name will respond and because SAMBA only sent out a NBNS and not DNS request, it will be satisfied with one response.  Away we go, worked very nice.  Hope it works as well for anyone needing this information.

---

