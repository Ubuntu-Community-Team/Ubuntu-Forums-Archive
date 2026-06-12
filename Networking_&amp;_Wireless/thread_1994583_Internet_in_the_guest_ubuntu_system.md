---
title: "Internet in the guest ubuntu system"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by java.jfan on 2012-06-03
Hi, 
At work I'm using a Windows 7 in some domain in our organization.

I've installed an ubuntu (10.10) as a guest machine using a virtual box (version 4.0.4)

When I work from home with my router that runs dhcp I get internet access from both Windows 7 and ubuntu machines.

However when I'm running an ubuntu while being at work, I can -get only to the "intranet" servers from Ubuntu and Windows 7 works great with internet as well.

As for the internet sites I can do 'nslookup' for example, but I can't really type neither dns name nor IP and load the site.

I guess its some sort of proxy or something but I don't really understand in computer networks to figure this out alone.

Any help will be highly appreciated :)

Thanks a lot in advance
Mark

---

### Post by Cheesemill on 2012-06-03
You should really ask IT Support at your workplace as we have no way of knowing how their network is set up.

There are several different situations which could be causing your VM to not have internet access and without knowing exactly which it is I'm afraid no-one here will be able to help.

---

### Post by java.jfan on 2012-06-10
Thanks a lot!
It took me quite a while... but I've talked to our IT guys. It turned out that all I needed to do is to configure the Network Proxy via the System --> Network Proxy Preferences and chose one of the proxies in the list in Ubuntu. So now I have an access to internet.

Now I have a conceptual misunderstanding of how things work.

When I set the proxy (I chose Proxy Configuration Tab -> Manual Proxy Configuration filled HTTP Proxy + Port and set the checkbox 'use the same proxy for all protocols') I can browse the internet sites (like this one), but for some reason I don't have a connection to our internal sites (it ok that the proxy server doesn't allow to get to these sites)
Whats weird is that things like nslookup work even for intranet sites, the dns servers are configured right (I've checked in etc/resolv.conf)

When I disable the proxy - the intranet stuff works, but internet doesn't

I admit I'm a complete newbie in computer networks, but how can I make both internet and LAN to work together? :)

Is it something I can do with Ubuntu or I should use another proxy or something?

In my windows 7 host machine we have scripts that configure the list of DNS servers and after running these scripts I have local intranet connections working. 
Internet works always perfectly...
Our IT guys don't really support ubuntu/linux virtual machines at all, so I would prefer to talk to them only when I'm out of hope :)

Thanks a lot and sorry for resurrecting the dead thread
Mark

---

### Post by java.jfan on 2012-06-10
Ok, it looks like I've managed to make things working by myself.
(Should have selected  automatic proxy configuration and not configure the proxy manually)

Thanks a lot for help!

---

