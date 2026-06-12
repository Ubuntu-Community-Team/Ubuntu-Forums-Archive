---
title: "Resolve hostname when using DHCP wireless router"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by emonette123 on 2010-11-17
Here is my configuration:

1 Wireless router, using DHCP, not DNS server capable
1 XUbuntu computer wired to the router
1 Puppy Linux old computer wirelessly connected to the router

So it is two Linux machines on one network, no samba needed, no WINS, no netbios.

I am having a hard time resolving hostnames for this.
No, I cannot use static IP addresses as it makes it stupidly awkward for people visiting to connect to my Wireless LAN.
No, I cannot set up a DNS Server on my XUbuntu machine because I cannot be sure of its IP address and also because it would have to be ON all the time.
No, I cannot use /etc/hosts since I cannot guarantee the IP addresses.

What frustrates me is my Router knows the hostnames of all computers (or devices) connected:  I can see them on the Web page of the router.

I guess the router uses the name sent by the DHCP client when connecting.

Is there a way to resolve these hostnames automatically?

I had a glimpse at zeroconf for Ubuntu, which would enable me to use hostname.local, but I do not think this is available on Puppy Linux...

Another solution would be to query the router for its DHCP table and update hosts, but this really difficult to manage.

---

### Post by misterspider on 2010-11-18
I know that in network manager you can set Automatic (DHCP) addresses only via Wired -> Edit -> IPv4 Settings -> Method drop down menu.
You can then specify your DNS servers manually. Does this help?

---

### Post by emonette123 on 2010-11-23
My problem is I cannot guarantee the IP address of any of my machines since they are all assigned via DHCP.
And I cannot disable DHCP since it makes my wireless network unusable.
My router doesn't allow me to reserve a specific address for a specific machine.
My router doesn't serve as a DNS, it only forwards the DNS of my internet provider.

So no, I cannot set my DNS servers manually.

Looks to me only mDNS and some Bonjour protocol will be my friend here.  I will have to find suitable packages for Puppy Linux and use hostname.local to access my computers.

---

### Post by pricetech on 2010-11-23
You can assign fixed IP addresses to your computers without turning off DHCP in your router.  Just assign addresses that are outside the scope.

Shame your router won't let you reserve IPs.  What brand and model ??  Just curious who would build such a thing ??

---

### Post by cybergnome on 2010-11-23
The fact that your router gives you IP leases for your machines (yes, they can change or be renewed), has nothing to do with your DNS servers.  They are assigned by your ISP, and yes, you can manually enter them, as suggested by others.  Clearly, if your system doesn't know the DNS servers addresses, it can't resolve host names.

If you can ping a web IP, but it's hostname is not resolved, the you have a DNS issue.

---

### Post by emonette123 on 2010-11-23
pricetech, you are my man...

Didn't know that.  So I can go static for my two static machine and still use DHCP for guests.  That is exactly what I needed and can now use /etc/hosts to resolve my two "static" computer on my network.  No need for a DNS here.
FYI:  router is Trendnet TEW-432BRP.  Paid like 10$ for the router and a wireless USB key a while ago, it was kinda given, so I cannot complain too much about the lack of features!

cybergnome, I was talking about resolving hostnames on a home network which is using DHCP over wireless...  Reaching my provider DNS was never an issue here.

---

### Post by pricetech on 2010-11-24
> **emonette123 said:**
> My router doesn't allow me to reserve a specific address for a specific machine.

That disappoints me.  I thought Trend was better than that.  What version do you have ??  There are 5 versions listed / illustrated on the page.

[http://www.trendnet.com/downloads/list_subcategory.asp?SUBTYPE_ID=955&SUBMIT=Go](http://www.trendnet.com/downloads/list_subcategory.asp?SUBTYPE_ID=955&SUBMIT=Go)

The last entry doesn't show any support for reserving IPs, but the first entry does.  They call it "Static DHCP".

Check your version, if you don't mind.  I'm more curious than anything else.

---

### Post by emonette123 on 2010-11-24
I have a rather old revision:  B1.0R

---

### Post by pricetech on 2010-11-24
Well dang.  I'm still disappointed in them.

Glad you got a solution that works for you though.

---

