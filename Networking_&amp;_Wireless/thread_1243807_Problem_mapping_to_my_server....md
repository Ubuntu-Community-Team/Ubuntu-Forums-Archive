---
title: "Problem mapping to my server..."
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by smcbryde on 2009-08-18
I've set up a home network for application development. I'm trying to map drives from my server to my computer, but I can't get it to work. I'll try to be as complete as possible in describing my network and anything that might be relevant.

Home network with a configuration as follows:

router (name: mynetwork.net)-->
-->Internet (cable)
-->computer1 (vista)
-->hub-->
----->computer2 (xp/sp3)
----->server (ubuntu 8.04, LAMP, ColdFusion, name: myserver)

computers 1 and 2 have DHCP issued ip addresses
server has static ip address: 192.168.0.110

When logged into the router firmware, both computers are listed under "LAN Computers", but the server is not shown.

I have no problem accessing the server using Webmin or phpmyadmin, and the web server works fine using its ip address: [http://192.168.0.110]("http://192.168.0.110/"), but NOT using the name: [http://myserver]("http://myserver/").

I need to map drives from the server to computer2 ("/var/www" & "/opt/coldfusion8").  

But when I try:

1. The server isn't shown under the browse button.
2. If I type anything like "192.168.0.110" or "\\myserver" or "mynetwork.net/myserver" or any combination I could think of, I get this message: "The drive could not be mapped because no network was found."

If I Run: \\192.168.0.110, I get this message: "No network provider accepted the given network path."

The Workstation service is set to "automatic" and is shown as "started".


Any insights would be very much appreciated, as I really need this to work.

Shane McBryde

PS. Do I need to be running the Samba file server in order to map to the server?

---

### Post by smcbryde on 2009-08-18
I've run across mention of SMB and smb.conf in connection with mapping, which seems to be associated with Samba. Do I need a file server on my server in order to map to it?

---

### Post by dtoronto on 2009-08-18
Are you using a router to traffic to set up your domain or do you have a DNS set up with bind.  Also is your server set up on a DHCP or static IP address.  The reason is that I have had some routers that will set up a quick and dirty DNS but only for IP's on a DHCP.  I ended up having to set everything up using bind9.

---

### Post by smcbryde on 2009-08-18
Hey, David. Thanks for responding.

Well, since I haven't a clue (even after googling it) what you mean by bind, I'd have to say the other.

It's just a simple home network with a router, feed the disk that comes with the router into each computer and presto.

The server has a static ip address (192.168.0.110) which I set in Ubuntu, while the two computers are assigned ip addresses by the router, restricted to: 192.168.0.100 to 192.168.0.109.

If that's of any help with your question. I'm new at all of this network stuff, but I'm getting the hang of a little part of it.

---

### Post by dmizer on 2009-08-18
Does the router configuration allow you to give the server a permanenet DHCP lease?

Since the server's IP is not assigned by the router, it's no surprise that nothing can see it.

---

### Post by smcbryde on 2009-08-19
Thanks for responding, dmizer.

That's one of the weird things I came across in the routers help docs. It talks about reserving an ip address (which resides within the set DHCP IP Address Range...which my server's address doesn't) for a device that needs to be manually configured, and even has an internal link to an anchor on the same page to this topic. But, the link doesn't go anywhere, the topic doesn't exist, and there doesn't seem to be any controls associated with this or, as you mentioned, controls for a permanent DHCP lease. 

But then, every tutorial I've come across about installing the Ubuntu server has instructed you to set the server ip address as static and in Ubuntu itself. So, this configuration must be commonplace. 

Shane

---

### Post by dmizer on 2009-08-19
It will work correctly if your entire network is static.

What router do you have?

---

### Post by smcbryde on 2009-08-19
wikipedia on SMB: [http://en.wikipedia.org/wiki/Server_Message_Block](http://en.wikipedia.org/wiki/Server_Message_Block)

States the following:

"In computer networking, Server Message Block (SMB) operates as an application-layer network protocol mainly used to provide shared access to files, printers, serial ports, and miscellaneous communications between nodes on a network."


And Ubuntu help on SettingUpSamba: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Opening statement reads in part:

"Samba is a set of tools to share files and printers with computers running Microsoft Windows. It implements the SMB network protocol, which is the heart of Windows networking."


So, in order to set up mapping between a Windows enviroment and an Ubuntu server, I would need Samba installed?

That's a question, by the way...

Shane

---

### Post by smcbryde on 2009-08-19
My router is: D-Link EBR-2310 Wired Ethernet Broadband Router.

---

### Post by dmizer on 2009-08-19
> **smcbryde said:**
> So, in order to set up mapping between a Windows enviroment and an Ubuntu server, I would need Samba installed?
Yes. But that's not as difficult as it sounds. All you need to do is right click on a folder you want to share and select "sharing options". Samba will be installed automatically.

The router's option for reserved DHCP addresses should be under: setup > network settings in your router's configuration page.

You'll have to allow your server to be assigned an ip address within the DHCP range. Then you can set a reserved DHCP address according to your server's MAC address. But with Samba, a static IP address isn't really necessary. It's helpful to be sure, but not essential.

---

### Post by smcbryde on 2009-08-19
Well, a little more difficult. I'm running Ubuntu server with no GUI. So, right clicking a folder is out. But I'll figure it out.

As for the reserving DHCP addresses, as I said, there are no controls for it, as shown:
[http://i676.photobucket.com/albums/vv125/skmcbryde/NetworkSettings.gif](http://i676.photobucket.com/albums/vv125/skmcbryde/NetworkSettings.gif)

The router help docs make mention of it, but the anchor from the link doesn't exist, nor does the actual topic the link is suppose to link to. And the router firmware is up to date.

But anyway, I've got the lead I needed about Samba. So thanks again.

Shane

---

