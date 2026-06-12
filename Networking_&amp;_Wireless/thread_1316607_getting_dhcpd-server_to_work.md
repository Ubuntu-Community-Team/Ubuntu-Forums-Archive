---
title: "getting dhcpd-server to work"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by dvdljns on 2009-11-06
I tried the how to on this forum and it still does not serve webpages. My comp said I was conected and my router said I was connected but no web. I would like someone that understands this to walk through it with me.

                         dhcp.conf



ddns-update-style interim
ignore client-updates
 
subnet 192.168.1.0 netmask 255.255.255.0 {
 > 

   # The range of IP addresses the server
   # will issue to DHCP enabled PC clients
   # booting up on the network
 
   range 192.168.1.201 192.168.1.220;
 

When my router sees the internet it changes it's range to 10.0.0.2 to 10.0.0.100 giving itself 10.0.0.1
all i need asigned is one ip to my router. my router then will asign the ip addresses to my comps.
My router also does translation to my comps.
It seems to me since my rouer sees the other router that it is not using my dhcp server.

> 
   # Set the amount of time in seconds that
   # a client may keep the IP address

  default-lease-time 86400;
  max-lease-time 86400;
 

can this be all 9's
> 
   # Set the default gateway to be used by
   # the PC clients
 


Heres where I think my problem is. The default gate seen by the router should be my dhcp server not the roadrunner gateway.

> 
   option routers 192.168.1.1;
   # Don't forward DHCP requests from this
   # NIC interface to any other NIC
   # interfaces
 
   option ip-forwarding off;


Ok!

 > 
   # Set the broadcast address and subnet mask
   # to be used by the DHCP clients
 
  option broadcast-address 192.168.1.255;
  option subnet-mask 255.255.255.0;
  
This should be changed to my address range right.

> 
   # Set the NTP server to be used by the
   # DHCP clients

  option ntp-servers 192.168.1.100;


I will use rr for now.

> 
   # Set the DNS server to be used by the
   # DHCP clients

  option domain-name-servers 192.168.1.100;
 

I use bind9 so I ned to research this. Also I installed a dns server that I may have remove?

> 
   # If you specify a WINS server for your Windows clients,
   # you need to include the following option in the dhcpd.conf file:

  option netbios-name-servers 192.168.1.100;
 

Need to research but if I don't know the answer is most likely no.

> 
   # You can also assign specific IP addresses based on the clients'
   # ethernet MAC address as follows (Host's name is "laser-printer":

  host laser-printer {
      hardware ethernet 08:00:2b:4c:59:23;
     fixed-address 192.168.1.222;
   }
}


have a lexmark printer with fax I would like to play with.

> 
#
# List an unused interface here
#
subnet 192.168.2.0 netmask 255.255.255.0 {
}



What and why.


Another thing he did in the how-to is ip fowarding from one interface to the other. but I do not know why. I seems to me that my router should only see my comp. not be routed to the other ethernet. Right now my router is asking the roadrunner gateway for a ip address not my dhcp server. Would route be abetter way to go. And how do I get eth1 to ask my dhcp server to assign it a ip unless my system is assigning it a ip. i.e. something to send requests to.

---

