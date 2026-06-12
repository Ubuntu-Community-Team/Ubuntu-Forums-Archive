---
title: "Ubuntu Server Documentation."
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by atif7865 on 2012-03-06
Hello guys,

I have been to this forum many times and unfortunately every time i have had bad experiences.

so here i go once more.

I need a detailed documentation on setting up dhcp server on ubuntu server. 
Please dont direct me to pages with 10 lines of code, I need a detailed version if there is any out there.

Thanks in advance.

---

### Post by jonobr on 2012-03-06
Wouldn't it be worse if you had to pay for it....

As you most likely know the configuration is mainly contained within the dhcpd.conf file within the /etc directory after you install the dhcp server.

[The man pages]("The man pages") contain a lot of detail about the options, how it works and so on.

The dhcpd.conf provides some details as well as examples but again, the manpages have a lot of useful information.

Im not sure if this addresses your problem (if you want to setup a single instance) or if your trying to do more or have a specific issue.

I get the feeling one way or the other, your dissapointed already.

---

### Post by atif7865 on 2012-03-06
> **jonobr said:**
> Wouldn't it be worse if you had to pay for it....

As you most likely know the configuration is mainly contained within the dhcpd.conf file within the /etc directory after you install the dhcp server.

[The man pages]("The man pages") contain a lot of detail about the options, how it works and so on.

The dhcpd.conf provides some details as well as examples but again, the manpages have a lot of useful information.

Im not sure if this addresses your problem (if you want to setup a single instance) or if your trying to do more or have a specific issue.

I get the feeling one way or the other, your dissapointed already.

Its not about getting disappointed. I need to fully and completely understand DHCP, what is wrong with that?
and why is so that there are no documentations about it. the man pages are great for a person who already knows it. it starts off by omitting the global parameters, so it assumes you know that. and it keeps assuming you know alot of things. 
I could find a good book on for example DNS, but nothing on DHCP. and dont get me wrong but I never expected anyone on this forum would hint any useful material. 
This has been my personal experience. it may be great for others. 
and as for as the talk of money,,, when did I say anything about linux ? or ubunut? I am talking about its online support. Have you ever been to for example Cisco's learningnetwork? well you will get a feel of what is a helpful forum.

ruling out the possibility of improvment is not productive at all.

just my two cents.

---

### Post by exodus_ on 2012-03-06
Maybe if you had a better attitude people would be more willing to help you?  Coming in here and saying "been here before and I don't really expect any help this time BUT..." is not really a great way to get support, IMO.

Have you tried to search for this information on say, google or another search engine?  A quick search showed me a few pages that might be of interest to you.

However, you need to help us to help you.

Thanks.

---

### Post by CharlesA on 2012-03-06
Does this help?
[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

> **exodus_ said:**
> Maybe if you had a better attitude people would be more willing to help you?  Coming in here and saying "been here before and I don't really expect any help this time BUT..." is not really a great way to get support, IMO.

Indeed. I was almost tempted to just jail it and ask them to repost with a different tone.

EDIT: @OP: If you feel you don't get any help on this forum, there are plenty of others out there. Maybe you'll find one that works for you.

---

### Post by Iowan on 2012-03-06
Have you seen the [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html")? This link is for 10.04, but there are others...

I run **dnsmasq** as a DHCP/DNS server.

---

### Post by CharlesA on 2012-03-06
> **Iowan said:**
> Have you seen the [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html")? This link is for 10.04, but there are others...

I run **dnsmasq** as a DHCP/DNS server.
+1. I used DNSmasq for my DNS server and the server documentation is pretty decent.

---

### Post by Jonathan L on 2012-03-07
> 
I need a detailed documentation on setting up dhcp server on ubuntu server. 


Dear Atif

Can I recommend Ralph Droms's and Ted Lemon's excellent DHCP Handbook?  (ISBN 0672323273) Covers pretty much everything you'll need.  As DHCP is a protocol, and one that works pretty well across different implementations, you'll find that understanding it at that level really helps when you then have to implement it on Ubuntu, Windows, Cisco, or whatever hardware is convenient.

The Ubuntu part is easy -- you install the software, edit the config file, and restart the DHCP.  The only tricky part is what to put in the config file.  And that of course depends entirely on exactly what kind of network you're running.  Here's a perfectly good description of how to do the basics: [http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)

If you're setting up DHCP for a network of any serious scale, do a lab set up first: if you make a mess of DHCP your network is off until you fix it.  Having said that, DHCP is usually a lot easier than DNS.

Hope that's helpful.

Kind regards,
Jonathan

---

