---
title: "Use local IP only on local network?"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by Whelk on 2010-05-25
I've got an Ubuntu server hosting our websites and other various things here in our own home.  We recently switched to a router that doesn't support loopback (abomination), so I've set up hosts files on our computers so we can access our own sites when on our home LAN.

However, we often take our laptops as we travel about, and I'm guessing due to the hosts files when we try to access our sites, it'll look on whatever local network we're connected to for our server, which won't work, obviously.

Is there a way to set up something like a hosts file that'll only try to look up the local IP of the server when we're on a specific network (our home one), or have one that tries to look for the local IP first, then proceeds to try and resolve the domain name and use the external IP if the local IP doesn't work?

---

### Post by linuxonbute on 2010-05-25
> **Whelk said:**
> I've got an Ubuntu server hosting our websites and other various things here in our own home.  We recently switched to a router that doesn't support loopback (abomination), so I've set up hosts files on our computers so we can access our own sites when on our home LAN.

However, we often take our laptops as we travel about, and I'm guessing due to the hosts files when we try to access our sites, it'll look on whatever local network we're connected to for our server, which won't work, obviously.

Is there a way to set up something like a hosts file that'll only try to look up the local IP of the server when we're on a specific network (our home one), or have one that tries to look for the local IP first, then proceeds to try and resolve the domain name and use the external IP if the local IP doesn't work?

What about 2 hosts files, one with the settings for your stuff at home and one without. Call one hosts.home and the other hosts.away
Then you can copy the appropriate one into your machine's host file.

---

### Post by Whelk on 2010-05-25
Thanks, that would work, though I was hoping for a more elegant (i.e. automated) solution.  I don't mind so much myself, but I'm sure the wife will be grumbling about the extra effort.

---

### Post by lykwydchykyn on 2010-05-25
Basically what you want is to run your own DNS server at home; that's what I do.  dnsmasq is a good option for this, as it can actually use the hosts file on the server instead of making you muck around in zone files.  It will forward non-local requests to your upstream DNS server (i.e., the one your ISP provides).

dnsmasq can be installed from the repos, and while it doesn't have a GUI or web interface, the configuration file is well documented and fairly straightforward.

Then you just set up your DHCP server (usually your router) to hand out the server's IP as the first DNS server, and whatever you're currently using as the second.  This way if the server is off for some reason, the internet will still be usable.

---

### Post by chili555 on 2010-05-25
How is /etc/hosts set up? In my home network, the server has a static IP, 192.168.1.101. The two computers of mine and my wife, have hosts files that include:```
192.168.1.101  myserver
```If we want to access the server, we open a browser and go to [http://myserver](http://myserver). We both have bookmarks.

---

### Post by Whelk on 2010-05-25
Great ideas.  I'll try setting up dnsmasq (I'm always glad to learn more about setting up my own stuff, hence why we run our own server) and if I get too confuzzed, I'll set up the separate 'myserver' entry in the hosts file to use when we're on the local network. Don't know why I didn't think of that.

Thanks!

---

### Post by Iowan on 2010-05-25
For what it's worth - I use DNSMasq for my network DHCP and DNS server. Clients who provide their hostname when requesting DHCP address can be referenced by hostname. Static leases (like printer and development web server) can also be referenced by name. As mentioned - non-local DNS requests are sent on upstream.

---

