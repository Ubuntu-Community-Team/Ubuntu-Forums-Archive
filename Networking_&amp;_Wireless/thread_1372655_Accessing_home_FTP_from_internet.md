---
title: "Accessing home FTP from internet"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by schmutztaucher on 2010-01-04
I have set up a FTP server in my home (FileZilla) and everything works how it is supposed to. I understand that port forwarding is required and can easily set that up. My question is what IP address do I use to connect to it when I am outside of my home network. Do I use the one my ISP gave me? And how do I figure out what that is? Could my ISP be using NAT that could be messing things up for me?

Could there any other configurations that I need to perform ? Also do ISP's frown upon home ftp servers? (USA)

Sorry for all the questions. I would greatly appreciate any and all help given.

-S

---

### Post by bluelamp999 on 2010-01-04
Check if you have a fixed IP address allocated by your ISP, though this is unlikely.

If you don't have a fixed IP address you can use a Dynamic Domain Name System service like DynDNS - [http://www.dyndns.com/](http://www.dyndns.com/)

DDNS allows you to access your network using domain names instead of IP addresses. The service manages changing IP addresses and updates your domain information dynamically. 

Your router may have a built in DDNS functionality (mine does as it runs DD-WRT) or you can download an update client to your machine.

Your router's home page should show you your IP address...

---

### Post by Barriehie on 2010-01-04
> **schmutztaucher said:**
> I have set up a FTP server in my home (FileZilla) and everything works how it is supposed to. I understand that port forwarding is required and can easily set that up. My question is what IP address do I use to connect to it when I am outside of my home network. Do I use the one my ISP gave me? And how do I figure out what that is? Could my ISP be using NAT that could be messing things up for me?

Could there any other configurations that I need to perform ? Also do ISP's frown upon home ftp servers? (USA)

Sorry for all the questions. I would greatly appreciate any and all help given.

-S

If you've got a dynamic IP then you'll have to go with some outfit like dyndns to update your IP to a hostname.  There are many outfits that do this, I've used for quite some time with no issues.  At that point you can simply point the outside computer to your domain name.  Note that most ISP's block most ports so you'll have to find out which ports aren't blocked and setup your FTP server to probably use a non-standard port.  You can go to [www.grc.com](www.grc.com) for a port scan to see what's blocked.  Once all that's in place you should be able to FTP into your machine.

If you've got a static IP then you'll still have to find out about which ports are blocked and can then continue.

---

### Post by pricetech on 2010-01-04
Use the IP address your ISP assigns to you.  If it's fixed, just make a note of it and use it.  If it's dynamic you'll need a service such as Dynamic DNS to tie a name to your IP so you can determine what it is when you're on the road.

They are probably not using NAT, but it is possible, just highly unlikely.  It's also possible that they are blocking ports 20 and 21, though I don't think many of them do that either.

Your ISP may frown on you having a FTP server but most won't care as long as the traffic doesn't get too excessive.  If you're just using it yourself and maybe sharing it with a couple of friends, then they probably won't care.  Check their Acceptable Use Policy to be certain.

Your biggest concern will be security.  Make sure you read everything you can get your hands on about FTP and how to secure it before you open yourself up.  A search of the forums and elsewhere should yield lots of good information.

---

### Post by schmutztaucher on 2010-01-04
Thanks for the help guys! luckily, I too am running DD-WRT on my router which already has Dynamic DNS. But I am unlucky in the fact that after further reading of my Fair Access Policy, I am prohibited to use DDNS of any kind. I also found out that I have a dynamic IP.  :(

Sorry to have wasted all your time.

-S

---

### Post by pricetech on 2010-01-05
I can't speak for anyone else, but my time was not wasted at all.  If you learned from it, all is good.

---

