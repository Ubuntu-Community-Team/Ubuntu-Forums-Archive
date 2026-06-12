---
title: "Mobile Broadband, VPN and Virtual Name Servers"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by Steve H on 2010-12-08
I've got an O2 PAYG Mobile Broadband USB dongle which I use to connect to the Internet when I'm out and about (takes a long time to become active; If anyone can help with that, that would be nice!). I connect to my Home network using a VPN (pptp), configured through the Network Manager. At home I'm running an Apache server on my network which is hosting some Virtual Name Websites, that I use for web dev. The sites are accessible when I'm at home on the wi-fi using hostnames (dev.templates.com; dev.drupal.com etc) so I know that internal name resolution is working.

The problem I'm having is that when I connect through the VPN I cannot connect to the Internet which I've worked out is due to the DNS not being forwarded. However, after much digging I discovered that if I check the "Use this connection only for resources on its network" (Network Connections/VPN/Edit/IPv4 Settings/Routes/..)then I can connect to the Internet but not the Apache hosted Virtual Name Sites via their hostnames. It does seem to look for them (usual browser progress bar) but nothing is visible in the browser.

Is it possible to get both working? So I can connect via the VPN to my Home network (accessing the network shares, Apache pages etc) while also being able to access the Internet.

I'm sure I'm missing something simple but any help would be great.

---

### Post by Steve H on 2010-12-10
Surely someone out there has some idea what is wrong with my VPN....

Come on people, don't let me down!!

---

### Post by messelink on 2010-12-10
What DNS server are you using to resolve the hostnames when you are on the local LAN? I am assuming your own DNS server, right? So you need to set up your mobile broadband internet connection to use your home DNS server.

Might be easier to make a few entries in your laptops /etc/hosts file though, that way you don't need DNS lookup to translate the urls to ip addresses. 

If you really need to you could dynamically change your hosts file whenever you connect online ([http://ubuntuforums.org/showthread.php?t=1642328](http://ubuntuforums.org/showthread.php?t=1642328)) but I don't think you will need that in this case.

---

### Post by Steve H on 2011-01-04
Messelink, thanks for answer. I've narrowed it down to a DNS issue as well but I'm confused what the next step is. The Server that I VPN to has it's HOSTs file pointing to the various Apache domains (virtual named host). The HOST file on my laptop is also configured so the Apache domains are listed against the Server's IP address.

Do I need to set up a DNS service on the server to get this to work? I seem to be able to view the internet over VPN (but no Apache pages) or view the Apache pages (but no internet). The only difference is that the latter has "Use this connection only for resources on it's network" unchecked (off).

This is still driving me crazy!!

---

### Post by Steve H on 2011-01-05
Finally got it working. I'd overlooked putting a route in the IPv4 routes. I put in a route from the router to the server as follows:

```

Address: 192.168.0.2
Netmask: 255.255.255.255
Gateway: 192.168.0.1
Metric: 0
```

And then checked the "Ignore automatically obtained routes" Bingo! It all works. The only thing that I hadn't tried was the Netmask: 255.255.255.255. I'd been putting 255.255.255.0, don't know if that makes a difference but it seems to in my case.

Thanks for help
):P

---

