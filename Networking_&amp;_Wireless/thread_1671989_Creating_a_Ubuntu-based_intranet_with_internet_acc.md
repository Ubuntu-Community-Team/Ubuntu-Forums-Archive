---
title: "Creating a Ubuntu-based intranet with internet access"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by zander x on 2011-01-20
Hello! This might not be the right place to post this, but I can't get any answers anywhere.

I am trying to create an intranet that will serve about 100 clients. If it is possible, I would like it to be set that anyone on the intranet would be able to type **helpdesk**in their browser bar and be taken to the intranet site. I have Webmin and there are just too many options to figure out how to do this. They may as well have written it in Chinese. File server? Email? Impossible.

I can get to the intranet locally by typing in the local IP, but no one wants to remember numbers.

Then, I need to get that intranet accessible via the internet. A domain name has already been purchased and our cable company has assigned us 5 static IPs. The issue here is getting the IP to link up with the server. The intranet has to be configured in such a way that it can be administered remotely. Again, with Webmin, I am clueless. I was going to try to use ISPConfig, but seeing as how you have to pay for the install directions, I figured to come here to ask for help. I posted at another forum where nearly 200 people viewed it and I still don't know what to do. 

Please help if you can. Thank you. You can even start with "reinstall Ubuntu server" because that is what I think I am about to do.

---

### Post by WthIteh on 2011-01-20
> **zander x said:**
> 
I am trying to create an intranet that will serve about 100 clients. If it is possible, I would like it to be set that anyone on the intranet would be able to type **helpdesk** in their browser bar and be taken to the intranet site.
You could do it by DNS A entries or using /etc/hosts of end-systems.
Of course DNS solution is better for handling 100 clients.
> **zander x said:**
> 
I have Webmin and there are just too many options to figure out how to do this. They may as well have written it in Chinese. File server? Email? Impossible.
Webmin has a good wiki. Try searching there, and you could find well-written instructions. For setting up the DNS (of helpdesk entry) you may use:
[http://doxfer.webmin.com/Webmin/BINDDNSServer#Adding_and_editing_records](http://doxfer.webmin.com/Webmin/BINDDNSServer#Adding_and_editing_records)
> **zander x said:**
> 
Then, I need to get that intranet accessible via the internet. A domain name has already been purchased and our cable company has assigned us 5 static IPs. The issue here is getting the IP to link up with the server.
You could configure static IP address for your servers via /etc/network/interfaces files.
Take a look at
```
man interfaces
```
or [http://doxfer.webmin.com/Webmin/NetworkConfiguration#Viewing_and_editing_network_inte](http://doxfer.webmin.com/Webmin/NetworkConfiguration#Viewing_and_editing_network_inte)

---

### Post by WthIteh on 2011-01-20
Duplicate post!

---

### Post by zander x on 2011-01-20
> **WthIteh said:**
> You could do it by DNS A entries or using /etc/hosts of end-systems.
Of course DNS solution is better for handling 100 clients.

Webmin has a good wiki. Try searching there, and you could find well-written instructions. For setting up the DNS (of helpdesk entry) you may use:
[http://doxfer.webmin.com/Webmin/BINDDNSServer#Adding_and_editing_records](http://doxfer.webmin.com/Webmin/BINDDNSServer#Adding_and_editing_records)

Thanks for this info. I followed it as best I could and I'm right back where I started from. **helpdesk** takes users to [http://www.google.com/search?aq=f&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=helpdesk](http://www.google.com/search?aq=f&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=helpdesk) . **localhost**, **localhost/**, and **system-server** dead-end me as well.

Even after I erase everything and start all over, if I tell BIND that this is for intranet only (one of the startup options), I'll still have the internet problem. :mad:

---

### Post by WthIteh on 2011-01-21
> **zander x said:**
> **helpdesk** takes users to [http://www.google.com/search?aq=f&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=helpdesk](http://www.google.com/search?aq=f&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=helpdesk) . **localhost**, **localhost/**, and **system-server** dead-end me as well.
This is your browser feature for finding correct answer.
When you enter a name in the URL box and browser could not resolve it, then the browser will search for that word (by google) to find your desired website.

So we could conclude that the name is not resolved (by DNS A entry).
You could use the **ping** command instead of your browser since now. Whenever ping could resolve correct IP address, you could use it in the browser too. You could also use **host** command to resolve DNS information of a name.

Two possible tests (after double checking that you have a correct DNS A entry as you want):

[LIST=1]
[*]On the server itself (which hosts BIND service) ping helpdesk
[LIST=1]
[*]If you could not ping here, DNS entry is wrong.
[/LIST]
[*]ping from another machine
[LIST=1]
[*]If you could not ping here, then the machine did not use that BIND service as its DNS.
[*]Check the DNS server IP address value on that machine.
[LIST=1]
[*]If that machine is ubuntu too, you could check it by
**cat /etc/resolv.conf**
[/LIST]
[/LIST]
[/LIST]

---

### Post by zander x on 2011-01-21
> **WthIteh said:**
> This is your browser feature for finding correct answer.
When you enter a name in the URL box and browser could not resolve it, then the browser will search for that word (by google) to find your desired website.

So we could conclude that the name is not resolved (by DNS A entry).
You could use the **ping** command instead of your browser since now. Whenever ping could resolve correct IP address, you could use it in the browser too. You could also use **host** command to resolve DNS information of a name.

Two possible tests (after double checking that you have a correct DNS A entry as you want):

[LIST=1]
[*]On the server itself (which hosts BIND service) ping helpdesk
[LIST=1]
[*]If you could not ping here, DNS entry is wrong.
[/LIST]
 
[*]ping from another machine
[LIST=1]
[*]If you could not ping here, then the machine did not use that BIND service as its DNS.
[*]Check the DNS server IP address value on that machine.
[LIST=1]
[*]If that machine is ubuntu too, you could check it by
**cat /etc/resolv.conf**
[/LIST]
 
[/LIST]
 
[/LIST]


Ok, so I had to start all the way over again, and now I am on a Dell PowerEdge 2650.

DNS A entry: I don't know where that goes because that phrase isn't mentioned anywhere.

If I **ping helpdesk** on this machine, this is what I get:

[I]lrb@lrbserver:~$ ping helpdesk
PING helpdesk (10.1.10.50) 56(84) bytes of data.
64 bytes from helpdesk (10.1.10.50): icmp_req=1 ttl=64 time=0.067 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=2 ttl=64 time=0.058 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=3 ttl=64 time=0.065 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=4 ttl=64 time=0.058 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=5 ttl=64 time=0.060 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=6 ttl=64 time=0.061 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=7 ttl=64 time=0.059 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=8 ttl=64 time=0.058 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=9 ttl=64 time=0.058 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=10 ttl=64 time=0.060 ms
^C
--- helpdesk ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8997ms
rtt min/avg/max/mdev = 0.058/0.060/0.067/0.007 ms
lrb@lrbserver:~$ [/I]

That's a step in the right direction. If I do that from another compuyter, I get 

*ping: unknown host helpdesk*

That machine happens to be Ubuntu as well, but the rest of the network is Win XP, Vista, 7 and a few Macs. So that last command yields:

[I]# Generated by NetworkManager
nameserver 68.87.73.242
nameserver 68.87.71.226[/I]

---

### Post by SeijiSensei on 2011-01-21
I'm afraid you're in for some serious study if you really want all this to work.

First, you'll need to set up a DNS server internally to handle requests for internal names.  Then you'll need to make sure all the internal hosts use that server for name resolution.  Probably you're getting the server information from your router via DHCP, especially since the nameserver addresses in resolv.conf are Comcast's. You'd need to change the router to make your new internal nameserver appear first in the list.

Frankly, if you've never done anything like this before, I recommend hiring someone knowledgeable about Unix/Linux networking to help you set everything up.  With 100 desktops, your firm must have enough resources to bring in some outside help.  This is a good example of why open-source doesn't mean costless.  The software may be free, but solid expertise costs money.  In the long run it's usually money well-spent, but some people see "free software" and think it's really "free."  It's not.  (Don't forget to value your own time in the process as well.  From an opportunity-cost perspective, your time isn't "free" either.)

---

### Post by zander x on 2011-01-21
> **SeijiSensei said:**
> I'm afraid you're in for some serious study if you really want all this to work.

First, you'll need to set up a DNS server internally to handle requests for internal names.  Then you'll need to make sure all the internal hosts use that server for name resolution.  Probably you're getting the server information from your router via DHCP, especially since the nameserver addresses in resolv.conf are Comcast's. You'd need to change the router to make your new internal nameserver appear first in the list.

Frankly, if you've never done anything like this before, I recommend hiring someone knowledgeable about Unix/Linux networking to help you set everything up.  With 100 desktops, your firm must have enough resources to bring in some outside help.  This is a good example of why open-source doesn't mean costless.  The software may be free, but solid expertise costs money.  In the long run it's usually money well-spent, but some people see "free software" and think it's really "free."  It's not.  (Don't forget to value your own time in the process as well.  From an opportunity-cost perspective, your time isn't "free" either.)

Thank you very much for that information.Time I've got, but money, they don't have much of...or at least not enough to justify the large bill that they would be receiving. That takes care of the intranet part. But, they could still use 10.1.10.50, couldn't they?

Now on to the internet part. I have 5 static IPs to work with and I will be connecting directly into the cable modem/router. What's next? I'm thinking I have to input my IP info into BIND and update my network info with NetFirms and then I should be good? Right or wrong? I appreciate the help.

---

### Post by WthIteh on 2011-01-22
> **zander x said:**
> Ok, so I had to start all the way over again, and now I am on a Dell PowerEdge 2650.

DNS A entry: I don't know where that goes because that phrase isn't mentioned anywhere.

You could find it as the first item at
[http://doxfer.webmin.com/Webmin/BINDDNSServer#Record_types](http://doxfer.webmin.com/Webmin/BINDDNSServer#Record_types)
> **zander x said:**
> 
If I **ping helpdesk** on this machine, this is what I get:

[I]lrb@lrbserver:~$ ping helpdesk
PING helpdesk (10.1.10.50) 56(84) bytes of data.
64 bytes from helpdesk (10.1.10.50): icmp_req=1 ttl=64 time=0.067 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=2 ttl=64 time=0.058 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=3 ttl=64 time=0.065 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=4 ttl=64 time=0.058 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=5 ttl=64 time=0.060 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=6 ttl=64 time=0.061 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=7 ttl=64 time=0.059 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=8 ttl=64 time=0.058 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=9 ttl=64 time=0.058 ms
64 bytes from helpdesk (10.1.10.50): icmp_req=10 ttl=64 time=0.060 ms
^C
--- helpdesk ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8997ms
rtt min/avg/max/mdev = 0.058/0.060/0.067/0.007 ms
lrb@lrbserver:~$ [/I]

That's a step in the right direction. If I do that from another compuyter, I get 

*ping: unknown host helpdesk*

Good :) I think that you are running your BIND server on 10.1.10.50 machine (If no use your BIND server IP address for the rest).
Before moving forward you could test with
```
host helpdesk
```
on the server. It should show you the DNS A entry information. If it does not so, you should return fixing DNS entry. If yes, you could continue testing on the other machine (your laptop with ubuntu).
> **zander x said:**
> 
That machine happens to be Ubuntu as well, but the rest of the network is Win XP, Vista, 7 and a few Macs. So that last command yields:

[I]# Generated by NetworkManager
nameserver 68.87.73.242
nameserver 68.87.71.226[/I]
For testing open that file for editing
```
gksu /etc/resolv.conf
```
and add this line to its beginning
```
nameserver    10.1.10.50
```
save it, and do the ping and host tests:
```

ping helpdesk
host helpdesk

```
If they were OK, you could continue with DHCP and making these changes permanent for all 100 client independent of their OS :)

Also do not become upset, best sysadmins were started at one time. Just keep moving forward.

---

### Post by zander x on 2011-01-31
> **WthIteh said:**
> You could find it as the first item at
[http://doxfer.webmin.com/Webmin/BINDDNSServer#Record_types](http://doxfer.webmin.com/Webmin/BINDDNSServer#Record_types)

Good :) I think that you are running your BIND server on 10.1.10.50 machine (If no use your BIND server IP address for the rest).
Before moving forward you could test with
```
host helpdesk
```
on the server. It should show you the DNS A entry information. If it does not so, you should return fixing DNS entry. If yes, you could continue testing on the other machine (your laptop with ubuntu).

For testing open that file for editing
```
gksu /etc/resolv.conf
```
and add this line to its beginning
```
nameserver    10.1.10.50
```
save it, and do the ping and host tests:
```

ping helpdesk
host helpdesk

```
If they were OK, you could continue with DHCP and making these changes permanent for all 100 client independent of their OS :)

Also do not become upset, best sysadmins were started at one time. Just keep moving forward.

Well I have been working on this project and I am running into walls at every turn. I decided to forego the intranet portion and instead work on the internet portion. I might as well be trying to cure HIV because at this point, I think it would be easier. I followed the directions on here and on this Youtube tutorial video ([http://www.youtube.com/watch?v=wMAlsPq6qTw](http://www.youtube.com/watch?v=wMAlsPq6qTw)) and it's still a no-go. Netfirms won't accept my new DNS info. MyPHPadmin has errors all over the place, and because there are soooo many options (SMC 8014), there's no clear-cut way to provision an IP address to the server, although I have figured out that it is best to connect this thing straight to the cable modem. One piece of literature said to disable DHCP over the LAN. Uh-huh. Then the modem stopped working. Then I left. Good thing it wasn't in the main network. Help. There are 7 billion people on this planet and I know I'm not the only one having problems.  I did this before years ago and I don't recall it being this difficult.

---

### Post by mips on 2011-02-01
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

What router are you using?

---

### Post by zander x on 2011-02-11
> **mips said:**
> [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

What router are you using?

SMC8014
Comcast Business Gateway

I've tried almost everything I can think of (including portforward.com), and 98.218.85.240 doesn't take me to where the server currently is, 10.1.10.90. However, I just noticed by static IP block has changed, but I still only get the modem login when I access 20.20.20.1.

---

