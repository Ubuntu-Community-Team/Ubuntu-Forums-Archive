---
title: "Tunneling through school AP"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by monkeylikestree on 2011-03-14
I am trying to tunnel through my college's free AP so I can get access to protocols outside of http and https. The school has an in-browser DNS redirect until you log in. 

 The output of "cat /proc/version" on the server OS is "Linux version 2.6.35-27-generic (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linar o 4.4.4-14ubuntu5) ) #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011" 

The client OS is Windows 7. What I have done so far is use Proxy Cap to redirect applications to a Putty tunnel connected to the server. Eventually I want to tunnel that SSH connection through my school's firewall, so that I can keep encryption and have a reasonable amount of ease with setup. 

I am not particularly educated on the inner workings of the DNS redirecting so I was not sure what to search for. My attempts to connect Firefox over normal http proxies failed and since all ports are blocked besides http and https I didn't attempt any socks or SSH. I have also tried simply hosting the SSH server on http ports with little success. 

I hope that I can do this without having to purchase a domain, but that's starting to seem like that won't be the case.

---

### Post by MattBD on 2011-03-14
Is this the kind of thing you're after?
[http://lifehacker.com/#!237227/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy](http://lifehacker.com/#!237227/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy)
Regarding the domain, you can get a free domain name via DynDNS - I use them with my PogoPlug that I've set up as a mail and web server, and it works well.

---

### Post by monkeylikestree on 2011-03-14
Not exactly. I can't connect to SSH behind this security. I cannot use a normal http proxy or a socks proxy to connect. I think the firewall is detecting the type of traffic going through. The reason I mentioned the domain name is because if I cannot manage to tunnel over http somehow I have seen some scripts that would allow me to tunnel over DNS, which would actually give me more anonymity than logging in. I want to avoid this because I suspect I'd take a shot in speed.

---

### Post by MattBD on 2011-03-14
OK, a quick Google search came up with a promising-sounding howto at [http://www.revsys.com/writings/quicktips/ssh-tunnel.html](http://www.revsys.com/writings/quicktips/ssh-tunnel.html)

---

### Post by monkeylikestree on 2011-03-14
I told you I can't connect through SSH. ._.
I want to tunnel SSH through another protocol, either http that works or DNS.
I am having trouble tunneling through http because the firewall seems to be blocking the traffic to regular http proxies.

---

### Post by MattBD on 2011-03-14
OK, I found a tutorial at [http://dag.wieers.com/howto/ssh-http-tunneling/](http://dag.wieers.com/howto/ssh-http-tunneling/) on tunnelling SSH over HTTP. Might be worth a try, but other than that I can't suggest anything else.

---

### Post by monkeylikestree on 2011-03-14
Thanks for the help.

---

### Post by monkeylikestree on 2011-03-14
I can't help but think there's a better way to do this. I may just be too ignorant to understand where to change that config, but I can connect to google and some other sites using their ip alone, so why should I need a domain to tunnel?

---

### Post by MattBD on 2011-03-14
I think the issue is that you need a static IP address or a domain name - most ISP's use dynamic IP addresses so it will be changing all the time. I use DynDNS to get a free domain name, and that works well. You may have to fiddle with your router at home to get it working, but many routers make it pretty easy to get DynDNS working with them - mine had the option to use DynDNS built in.

It's just occurred to me that maybe AjaxTerm might be another way to do what you want? It's a web-based terminal you can install and run on your server, and if you ran it on port 80 or port 443 and had your home router forward that port to the server, you could probably connect to it fine since it would just be another web server. You'd need a static IP address or domain name to be able to connect remotely, but that's not hard to get.

If there are things you want to access from college, it'd then be just a case of picking out apps that will do that from the command line.

---

