---
title: "use OpenBSD as a router and firewall"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by e24ohm on 2009-03-11
Folks:
I have an older IBM box that I have dumped 4 networks cards into the system. My main goal is run OpenBSD and turn the box into a VPN Gateway/Router/Firewall. I know this is not a ubuntu install, but since everyone is so helpful, i thought i would ask.

Does anyone have procedures on how to configure a setup of this type or can someone point me in the right direction?

Also, would it be easier for me to use Cent OS, Ubuntu or Fedora for this model?

Thank you,
E

---

### Post by Iowan on 2009-03-11
[http://blog.scottlowe.org/2006/10/06/openbsd-as-a-simple-nat-router/]("http://blog.scottlowe.org/2006/10/06/openbsd-as-a-simple-nat-router/")
I found a few more on Google with "openbsd router"

---

### Post by e24ohm on 2009-03-12
> **Iowan said:**
> [http://blog.scottlowe.org/2006/10/06/openbsd-as-a-simple-nat-router/]("http://blog.scottlowe.org/2006/10/06/openbsd-as-a-simple-nat-router/")
I found a few more on Google with "openbsd router"Hey, thanks mate...looks pretty.

Have you deployed linux in this type of model before?

thank you...Cheers!!!
E

---

### Post by executor on 2009-03-12
it`s not bsd check this out [http://www.smoothwall.org/](http://www.smoothwall.org/)

---

### Post by e24ohm on 2009-03-12
> **executor said:**
> it`s not bsd check this out [http://www.smoothwall.org/](http://www.smoothwall.org/)This looks nice. Have you personally played around with this product? If so, what do you like about it, and what don't you like about it. ]

I usually work form the cisco cli, and only recentlly started to learn linux to help my career, and I read about linux firewalls, routers, and vpn gateways. Thought i might play around with them.

Thanks.
E

---

### Post by albinootje on 2009-03-12
> **e24ohm said:**
> Folks:
I have an older IBM box that I have dumped 4 networks cards into the system. My main goal is run OpenBSD and turn the box into a VPN Gateway/Router/Firewall. I know this is not a ubuntu install, 
--- cut --
Also, would it be easier for me to use Cent OS, Ubuntu or Fedora for this model?

I find your question a bit confusing. You want OpenBSD (which is not Linux!), but then ask about CentOS,Ubuntu,Fedora.

Apart from that it depends on what you exactly want to do.
I prefer m0n0wall on some of my firewalls at work, because I like the GUI, it's fairly easy to set up, I like the fact that it uses FreeBSD, it works great on Soekris machines, and it does what i want and need. [http://m0n0.ch/wall/](http://m0n0.ch/wall/)
And in m0n0wall I've configured a separate group for two other colleagues to login to the GUI interface just to be able to ping, and see the logfiles, and nothing more, just for troubleshooting, I think that's a cool feature to have build in.

If you want more than m0n0wall offers, then take a look at pfSense : [http://en.wikipedia.org/wiki/PfSense](http://en.wikipedia.org/wiki/PfSense)

---

### Post by ussndmac on 2009-03-12
I've been using OpenBSD for my firewall/router for years.

Love it!

Mac

---

### Post by e24ohm on 2009-03-12
> **albinootje said:**
> I find your question a bit confusing. You want OpenBSD (which is not Linux!), but then ask about CentOS,Ubuntu,Fedora.

Apart from that it depends on what you exactly want to do.
I prefer m0n0wall on some of my firewalls at work, because I like the GUI, it's fairly easy to set up, I like the fact that it uses FreeBSD, it works great on Soekris machines, and it does what i want and need. [http://m0n0.ch/wall/](http://m0n0.ch/wall/)
And in m0n0wall I've configured a separate group for two other colleagues to login to the GUI interface just to be able to ping, and see the logfiles, and nothing more, just for troubleshooting, I think that's a cool feature to have build in.

If you want more than m0n0wall offers, then take a look at pfSense : [http://en.wikipedia.org/wiki/PfSense](http://en.wikipedia.org/wiki/PfSense)I didn't know that OpenBSD was not Linux. Is OpenBSD Unix then? If this is the case, how different are the commands? What are other version of Unix? Only version of Unix I knew of is Solaris, by SunMicrosystems, and i thought this was the only current Unix release in the wild; however, I just started learning about Linux and Unix, and currently run Fedora and Ubuntu. I found it easier to use Fedora for my Linux+ studies.

Thank you for the links, and recommendation on software. I hope to try this product out this weekend. Currently I am just collecting input, which I can use to build an idea or model on paper, and then deploy in a test enviornment.

Cheers!!!
E

---

### Post by e24ohm on 2009-03-12
> **ussndmac said:**
> I've been using OpenBSD for my firewall/router for years.

Love it!

Mac Is it preatty easy to configure? I am not looking at deploying IS-IS, or OSPF - just some static routes would be nice. Oh hey mate, does it support routing on a stick with vlan trunking?

---

### Post by albinootje on 2009-03-12
> **e24ohm said:**
> I didn't know that OpenBSD was not Linux. Is OpenBSD Unix then? 

OpenBSD, just like FreeBSD and NetBSD is a Unix-alike just like Linux, except with a different code-base. Linux was written from scratch, after Linus Torvalds got frustrated about Minix.
See here for more information about the background from BSD : [http://en.wikipedia.org/wiki/BSD](http://en.wikipedia.org/wiki/BSD)
> 
If this is the case, how different are the commands? 

I can give you some examples in commands between Linux and FreeBSD :
In FreeBSD the command "free" doesn't exist.
The sometimes very useful command "watch" in Linux, does exist in FreeBSD but does something different.
But in general a lot is pretty much the same or alike.
> 
What are other version of Unix? Only version of Unix I knew of is Solaris, by SunMicrosystems, and i thought this was the only current Unix release in the wild; however, I just started learning about Linux and Unix, and currently run Fedora and Ubuntu. I found it easier to use Fedora for my Linux+ studies.

There's Solaris, HP-UX, IBM's AIX, SCO (cough..) UNIX and perhaps more : [http://en.wikipedia.org/wiki/Unix#Branding](http://en.wikipedia.org/wiki/Unix#Branding)
> 
Thank you for the links, and recommendation on software. I hope to try this product out this weekend. Currently I am just collecting input, which I can use to build an idea or model on paper, and then deploy in a test enviornment.

No problem, good luck! m0n0wall is fairly easy to set up, and you can (amongst others) choose between using only a hard disk, or only cdrom+floppy (no hard disk), or compact-flash only.
Installing and configuring OpenBSD is really not that easy, and getting the default firewall software up and running takes some reading and/or research.
Compared to that m0n0wall is a breeze.

---

### Post by e24ohm on 2009-03-13
> **albinootje said:**
> OpenBSD, just like FreeBSD and NetBSD is a Unix-alike just like Linux, except with a different code-base. Linux was written from scratch, after Linus Torvalds got frustrated about Minix.
See here for more information about the background from BSD : [http://en.wikipedia.org/wiki/BSD](http://en.wikipedia.org/wiki/BSD)

I can give you some examples in commands between Linux and FreeBSD :
In FreeBSD the command "free" doesn't exist.
The sometimes very useful command "watch" in Linux, does exist in FreeBSD but does something different.
But in general a lot is pretty much the same or alike.

There's Solaris, HP-UX, IBM's AIX, SCO (cough..) UNIX and perhaps more : [http://en.wikipedia.org/wiki/Unix#Branding](http://en.wikipedia.org/wiki/Unix#Branding)

No problem, good luck! m0n0wall is fairly easy to set up, and you can (amongst others) choose between using only a hard disk, or only cdrom+floppy (no hard disk), or compact-flash only.
Installing and configuring OpenBSD is really not that easy, and getting the default firewall software up and running takes some reading and/or research.
Compared to that m0n0wall is a breeze.Mate, you have been a big help, and this is so great...Cheers!!!

will tell you how it goes this weekend.

---

### Post by executor on 2009-03-13
> **e24ohm said:**
> This looks nice. Have you personally played around with this product? If so, what do you like about it, and what don't you like about it. ]

I usually work form the cisco cli, and only recentlly started to learn linux to help my career, and I read about linux firewalls, routers, and vpn gateways. Thought i might play around with them.

Thanks.
E

i use it as a firewall and DHCP server, and for my use it has ben perfect. no problem at all. easy to install and manage

---

### Post by e24ohm on 2009-03-14
> **executor said:**
> i use it as a firewall and DHCP server, and for my use it has ben perfect. no problem at all. easy to install and manageHmmm, this is a nice idea to move my DHCP server off my server 2003 DC. Hmmmm - what do you think of running DHCP/DNS on one box and running another as a Firewall?

What I am trying to do is the follwoing

Internet <cisco 2600> ----- <firewall>----<switch0>----<Router>----switch---

firewall will be ASA with a DMZ

switch0 will have LAN1 and port mirroring and wireshark

Router will be my Openbsd box

switch will be a standard cisco 2950 for LAN2


Thank you,
E

---

