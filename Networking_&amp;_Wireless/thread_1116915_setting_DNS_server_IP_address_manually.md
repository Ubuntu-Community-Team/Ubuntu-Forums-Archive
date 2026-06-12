---
title: "setting DNS server IP address manually"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by wallywally on 2009-04-05
I have been using a VPN (Witopia PersonalVPN) on Hardy/Intrepid/Jaunty but my ISP has recently taken to blocking some sites from me (:mad:) by using their Domain Name Systems and as a result I need to set my DNS server manually in order to fully connect to the VPN.

Win/Mac instructions for this are on the Witopia wiki here: [http://www.wiki.witopia.net/wiki/FAQ](http://www.wiki.witopia.net/wiki/FAQ) (see Q6 ... *Although Automatic assignment using DHCP is the best method, you can also try setting our DNS server IP address manually. The IP addresses are 38.119.98.220 or 216.93.191.228.* ) but I have no idea how to do this in Ubuntu.

Any pointers or clues would be much appreciated.

---

### Post by netztier on 2009-04-05
> **wallywally said:**
> but I have no idea how to do this in Ubuntu.


Assuming that you are using network-manager for your local wired or wireless LAN access, do this:

right-click on NM's applet in the Gnome Panel, then -> Edit connections.

From the "wired" or "wireless" tab, select the connection entry that applies and press the "Edit" button.

[SIZE="1"][INDENT]On a side note: While you're at it, consider creating a *new* connection entry, duplicating the existing one, name it something meaningful, like: "home LAN with special DNS" or so. Then leave the normal connection profile as it is, and modify the new one as described below. Then you can switch between profiles with a click of a mouse in NetworkManager's Panel applet.
[/INDENT][/SIZE]

On the IPv4 Settings tab, switch the "Method" from *Automatic (DHCP)* to *Automatic (DHCP) adresses only*, and enter the IP addresses of the DNS servers you whish to use in the appropriate field below. "Search Domain" and "DHCP Client ID" may remain empty.



A totally **different approach** (although more advanced): you might go and find the file /etc/dhcp3/dhclient.conf, and remove the "#" from the line "prepend domain-name-servers" and put in the IP addresses of the DNS server you wish to use instead of 127.0.0.1 . If youd do, don't forget to include a ";" at the end of the line.

```
#prepend domain-name-servers 127.0.0.1;
```


regards

Marc

---

### Post by wallywally on 2009-04-05
> **netztier said:**
> A totally **different approach** (although more advanced): you might go and find the file /etc/dhcp3/dhclient.conf, and remove the "#" from the line "prepend domain-name-servers" and put in the IP addresses of the DNS server you wish to use instead of 127.0.0.1 . If youd do, don't forget to include a ";" at the end of the line.

This "more advanced" approach seems easier than using NM!  In any case I tried both to no avail.

However, I'm not really sure how to test it though other than to confirm that, for example, YouTube is still being blocked by my ISP.  I can see that my dhclient.conf file is changed to the Witopia West Coast DNS and I am able to connect to the Witopia VPN with openvpn so that I have a US IP address (and I can use this to view, for example, Hulu) but given that this is the case I don't understand how I am still being blocked out of some sites.

---

### Post by netztier on 2009-04-06
> **wallywally said:**
> This "more advanced" approach seems easier than using NM!  In any case I tried both to no avail.

However, I'm not really sure how to test it though other than to confirm that, for example, YouTube is still being blocked by my ISP.  I can see that my dhclient.conf file is changed to the Witopia West Coast DNS and I am able to connect to the Witopia VPN with openvpn so that I have a US IP address (and I can use this to view, for example, Hulu) but given that this is the case I don't understand how I am still being blocked out of some sites.

Maybe I left the most obvious question out of scope: are you actually using **DHCP** to get an IP address and information about DNS? Of course, above methods only work if you do. If have a mobile broadband connection, you're probably using **PPP** instead of DHCP.

And then: Neither dhclient nor Network-Manager or resolvconf should ever change /etc/dhcp3/dhclient.conf. Network-Manager or dhcpclient will however rewrite **/etc/resolv.conf**, and that is where you'll find the currently configured DNS servers.

DNS blocking is a braindead way to block acces to some sites (which is why for example the German government is considering to force the ISPs to implement it *hrhrhr*), since it can be circumvented with ease, as you can see from the suggestion. 

There are other ways to block site access than DNS; for example transparent proxies, or deep packet inspecting firewalls. Chances are that your ISP is more clever than the German government.

To see if your ISP actually fiddles with DNS, you can query different DNS servers with **dig**, whithout having to change configurations in the first place:

```
dig @<dns-server-ip> www.somedomain.com
```

And then see if you get different replies from different DNSs.


regards

Marc

---

### Post by wallywally on 2009-04-06
Success!

Thanks for the dig advice.  Playing around with dig I found that whilst I am evidently getting blocked out by my ISP and for some reason also when using Witopia's west coast server, I can access everything via their east coast server.    I have therefore pointed my resolv.conf to that.

Cheers Marc!

---

