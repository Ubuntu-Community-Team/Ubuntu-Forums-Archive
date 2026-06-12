---
title: "Network hostnames"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by rules on 2009-12-25
Hi all

Have been playing around setting up printer sharing across our network (XP, OS X, Ubuntu) and was wondering ...
7
Why can't I use/see hostnames? I always have to use the IP's or it will not see/find the machine.

Thanks.

---

### Post by capscrew on 2009-12-25
> **rules said:**
> Hi all

Have been playing around setting up printer sharing across our network (XP, OS X, Ubuntu) and was wondering ...
7
Why can't I use/see hostnames? I always have to use the IP's or it will not see/find the machine.

Thanks.

You need to have some name service running in the LAN to map hostnames to IP addresses.  This can be DNS (either /etc/hosts or a local DNS server) or NetBIOS.  NetBIOS is really for Windows hosts, but Samba on Linux and OS X will recognize it.

---

### Post by rules on 2009-12-25
A local DNS sounds like the solution (ie. something new to play with :)), but how do I go about it (typed dns into Synaptic and all the goodies that it displayed, didn't really make sense to me :P)? I have a machine which I'm using as my print server (which is part of the reason I would prefer to use host names instead of IPs).

How will this effect my "internet" as I have to specify a dns manually on my Karmic pcs otherwise nothing works (except for firefox :confused:).

Thanks.

---

### Post by capscrew on 2009-12-26
> **rules said:**
> A local DNS sounds like the solution ... 
[B]ut how do I go about it ...? 

I have a machine which I'm using as my print server (which is part of the reason I would prefer to use host names instead of IPs).

How will this effect my "internet" as I have to specify a dns manually on my Karmic pcs otherwise nothing works (except for firefox :confused:).

Thanks.

The first thing is how deep do you wish to go. By that I mean how complex a local DNS setup do you want (need)?  Are you using a router such as Netgear, Linksys, D-Link or the like?  If so you should be able to setup "local DNS" on that device.  

If not we can: ```

a. Manually map all hostnames in /etc/hosts files

b. Setup a simple DNS server that maps the LAN and 
forwards all internet requests for resolution to your 
ISP's DNS servers (i.e DNSmasq).

c. Setup a very complex local DNS server that also 
forwards non-local requests (i.e BIND9).

```

Option a. is the most simple if all we are doing is mapping a few hosts (computers) names to their respective IP addresses. In this setup we can use the **/etc/hosts** files on the Linux hosts and the **C:\Windows\System32\drivers\etc\hosts **file on windows hosts to map the local LAN.  The advantage to this is no additional software to install and configure.  The downside is you need to configure this file and **every host in the LAN**.

Option b. provides more flexibility.  All LAN side DNS requests are handled in one spot (the DNSmasq server).  DNSmasq can be setup to forward all WAN side DNS requests to the WAN side DNS server of your choice.  In addition it will cache those requests locally for faster response times.

Option c. is really no option for home use.  It is complex and really designed for enterprise use.  It will provide the home LAN user no added benefit over option b.

So the decision is really up to you.  I would check to see if you have the capability already in your router. 

I prefer the DNSmasq solution.  So do Netgear, Linksys, D-Link.  They all incorporate DNSmasq code.  DNSmasq  is available in synaptics if you want to install your own server.  

Make sure you install it on a host that is always up (running) if others are relying on DNS too.  Information is available at: [**_[COLOR="DarkSlateGray"]http://www.thekelleys.org.uk/dnsmasq/doc.html[/COLOR]_**]("http://www.thekelleys.org.uk/dnsmasq/doc.html").  

The documentation needed to configure the server is available at: [**_[COLOR="DarkSlateGray"]http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html[/COLOR]_**]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html").

A fully annotated copy of the conf file is available here: [**_[COLOR="DarkSlateGray"]http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example[/COLOR]_**]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example").

---

### Post by Iowan on 2009-12-26
+1 **dnsmasq** So far, I like it as my network DNS/DHCP server.

---

### Post by rules on 2009-12-27
I had a look through my D-Link router and it does not seem to have any local dns settings. I did find a place where I could assign "static" IP's using the mac addresses, which is already helpful, atleast I will always know what the server's IP is (tried disabling dhcp before and manually putting in IP's but then there is always some issues with the network). 

DNSmasq looks like the perfect solution although I had a look through the links and it all seems Greek to me #-o

---

### Post by capscrew on 2009-12-27
> **rules said:**
> I had a look through my D-Link router and it does not seem to have any local dns settings. 
Before we give up on this aspect, I would like to see what is really available.  What is the model number of your D-Link router?> 

I did find a place where I could assign "static" IP's using the mac addresses, which is already helpful, atleast I will always know what the server's IP is (tried disabling dhcp before and manually putting in IP's but then there is always some issues with the network). 

DNSmasq looks like the perfect solution although I had a look through the links and it all seems Greek to me #-o

There are a number of DNSmasq howto's on the internet.  See my search [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.google.com/search?q=dnsmasq+howto&btnG=Go!").  I understand you dilemma.  The writer tries to be succinct and in doing so needs to use "jargon".  If author did not then they would have to explain the explanation.  

See if my  search provides you any insight.

---

### Post by rules on 2009-12-27
Hi cap

It's a D-Link DSL G604T router.

Quickly went through a couple of sites and some of them are a little more idiot proof than others, but I'm sure I'll get it eventually. Just need to make some time and focus :)

Thanks for the help so far :wink:

---

### Post by capscrew on 2009-12-28
> **rules said:**
> Hi cap

It's a D-Link DSL G604T router.

You're right.  The router does not havethe ability to provide LAN side DNS. > 

Quickly went through a couple of sites and some of them are a little more idiot proof than others, but I'm sure I'll get it eventually. Just need to make some time and focus :)

Thanks for the help so far :wink:

So onward we proceed.  :D

---

### Post by rules on 2009-12-30
Hi cap

Been playing with dnsmasq on and off for the last 2 days (after finding a more user friendly site with instructions :)) and got it working, between my 2 Ubuntu machines anyway. The wife's Mac and the windows machine is another story. The Mac does not take kindly to manual changes being made to it's files and just reverts them and the Windows machine for some reason will recognise the one machines name but not the other.

Anyway, after thinking all of this over, I more than likely can eventually get all of this right, but, in a week and a half's time I go back to work and then I'll have to plug into a million other networks, which more than likely means I would have to scrap all my hard work. So for now, I'll stick to the router issuing "static" dhcp IP's. 

Thanks for the help and the info, always nice to learn something new :)

Cheers.

---

