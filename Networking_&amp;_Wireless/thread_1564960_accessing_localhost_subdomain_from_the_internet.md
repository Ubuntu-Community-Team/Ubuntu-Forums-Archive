---
title: "accessing localhost subdomain from the internet"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by tunist on 2010-08-31
Greetings!
I am relatively new to Ubuntu and linux in general... and have been playing with it for website development on my laptop at home.
I have successfully setup the server to serve a web project I am working on and it is accessibly via a subdomain on localhost (locally, obviously).. the project is inside folders within /var/www/

I now want to make that subdomain accessible from the internet to share the project with other people.. I have made the relevant router changes and the base PHP folder /var/www/ is accessible from the web when I visit my IP. However, when I attempt to access one of the subdomains (i.e. [http://subdomain.myip](http://subdomain.myip)) I have setup I get a 'Server not found' error in the browser (Firefox). I  also see the same error if I attempt to navigate to the project subfolder instead of the subdomain.. i.e. [http://myip/projectname](http://myip/projectname).

Can anyone point me in the direction of how to resolve this?
I've looked in the apache2 logs but don't see anything that is obviously helpful to me.

the subdomains are setup by way of adding entries into the 'hosts' file and I have also created files in the 'sites-available' folder for each of the projects/folders/subdomains.

cheers

p.s. I'm using the standard version of ubuntu, not the server, if that makes any difference.

---

### Post by MaindotC on 2010-08-31
Do you have a domain name pointing to the web server?  What is the name of the domain?

---

### Post by BkkBonanza on 2010-08-31
You said you added the subdomains to your hosts file. That's fine and why it works for your local machine. 

To have domains and subdomains work publicly on the internet you have to, first, own the domain name, then have it's name served by some DNS server on the web (or on your server accessible from the web), and also add the subdomains to that same DNS server, as either A records or CNAME records pointing at the main domain's IP. Subdomains don't automatically go there. You can usually add a "*" subdomain if you want to catch all of them though.

After that, if you can reach the main domain then the only thing that would prevent subdomains as well would be not having the subdomains configured in Apache's conf.

---

### Post by tunist on 2010-08-31
thanks for the replies. :)

I do own several domain names but presently none are pointing to my home development machine.

presently my home pc (the 'server' in question) is accessible from the internet via IP address.. so I take it from your replies that even if that is the case I cannot setup a subdomain without routing and registering with a DNS server?

if that is the case then I have another question if you don't mind answering.. 

The domain name I would most likely create a subdomain 'under' that would point to my home pc is presently routed to a rented webserver.. is it possible to configure the domain (DNS records) so that the main domain still points to the rented webserver and the subdomain points to my home pc?

thanks again

---

### Post by MaindotC on 2010-08-31
> **tunist said:**
> presently my home pc (the 'server' in question) is accessible from the internet via IP address.. so I take it from your replies that even if that is the case I cannot setup a subdomain without routing and registering with a DNS server?

I'm not sure if this is what you're doing but just so you know - you can't access a subdomain via IP address (or at least I do not know of such a process and if you could, I doubt you have that configured).  For example my home machine with a drupal subdomain installation is listed at [http://drupal.manner18.com](http://drupal.manner18.com) (it was a free domain I have no idea what manner18 is).  You can do an nslookup for manner18.ccom and it will tell you the ip address.  However, I cannot access the subdomain by typing drupal.<ipaddress> - if that's what you were trying to do.  DNS will point your request to the ip address that matches the domain name, and that is stored in something called an address record (or A record).  Once your request is sent to the ip address of the server you are requesting, then it is the responsibility of the server to determine if you are requesting web pages from the subdomain.  It's a little more complicated than that but that's the gist.  So, you need a domain name to access a subdomain and I apologize in advance if there is a way to do that of which I am not aware.

> is it possible to configure the domain (DNS records) so that the main domain still points to the rented webserver and the subdomain points to my home pc?

To my knowledge, this is not possible because DNS must have a record that matches an IP address to a domain.  So even if you request a subdomain, the DNS server will first tell the requesting machine the ip address of the requested domain, and the requesting machine will contact that webserver.  Now, the webserver could be configured to have the subdomain on a network share, which would require access to the webserver hosting the pages of the requested IP address.

---

### Post by tunist on 2010-08-31
ah ok I see.. I just went to point a spare domain to the address and found that I have to wait for the domain registration company to change something before I can update the DNS record..

the reason I want to do this at all is so that I can access the website on a windows machine on my home network.. I haven't managed to get ubuntu to recognise the windows 7 machine yet.. so I'm not sure whether I'll be able to access the localhost subdomain via the home network on the windows machine.. If I can then I'll probably skip the DNS update for now.. do you know if that will work (assuming I can get ubuntu and windows to communicate)?

thanx

---

### Post by BkkBonanza on 2010-08-31
Yes, if you use an A record for the subdomain DNS then it can point to a different IP then the main domain. This is used all the time by larger companies to host subdomains on various different servers. 

localhost is always the current machine. So you cannot access another machine on your network with localhost. You would need to set the hosts file on the Windows machine to be set to the IP of the Ubuntu machine just like you did before. The hosts file on Windows is in... well, it's been a while now, under \windows\system... ummm, just search under there it's hidden down a bit further.

A better way is to add the domain/subdomain to your router as a static DNS entry but not all routers support that so it depends on yours. Then it gets served to your whole network (assuming your router is used for DNS resolution, which is usually the case if using DHCP).

---

### Post by MaindotC on 2010-08-31
> **tunist said:**
> the reason I want to do this at all is so that I can access the website on a windows machine on my home network.. I haven't managed to get ubuntu to recognise the windows 7 machine yet.. so I'm not sure whether I'll be able to access the localhost subdomain via the home network on the windows machine.. If I can then I'll probably skip the DNS update for now.. do you know if that will work (assuming I can get ubuntu and windows to communicate)?

thanx

DNS updates usually take 24 hours because there is a setting in their configuration files to update their records at specified intervals, usually 24 hours.  Each DNS server connected to the internet updates its records by communicating with all the other DNS servers on the internet, in a hierarchical fashion, unless it has been configured differently - that's just how DNS works.  If you wanted to you could make your own DNS server that would host the records for the domain of your choosing, assuming it was purchased from a registrar, and that DNS server would become part of the internet just like all the other DNS servers world wide.

You mentioned this concept of a windows machine accessing a Ubuntu machine.  You're in web development so I would think you know this but just in case - web pages are usually served using open standards that are able to be interpreted on any machine that complies to those standards, which is pretty much anything.  I understand your concern about ACCESSING those webpages via DNS but once you get that settled then retrieving those web pages won't be a problem on any platform.

---

### Post by tunist on 2010-08-31
ok, I thought it was possible to route a subdomain to another server, yes.. I may have done it before on another project a few years back and am not recalling the exact details.

I just looked in my router config (netgear) and it only has dynamic DNS and 'static routes' option, which doesn't seem to be the same as static DNS... perhaps it is, I'll find the manual in a bit.

so.. if I set a domain's 'subdomain A record' in the  DNS to point to my local IP.. how do I setup the local apache config to get the traffic routed to the correct project?
is it possible to get apache to look at the referring address (i.e. [http://subdomain.mydomain.com](http://subdomain.mydomain.com)) and to then auto route that to the relevant subdomain on my local pc? (rather than apache serving the pages from the default server location - non-subdomain).

---

### Post by BkkBonanza on 2010-08-31
> **tunist said:**
> 
how do I setup the local apache config to get the traffic routed to the correct project?

If it works with your local machine then this must already be done. It's handled by the NameVirtualHost feature and creating a config for each subdomain that tells it which directory to use for it's files.

Also note, most decent DNS servers nowadays will update very quickly. Mine at name.com usually takes a few minutes. It used to be that they took 24-72 hours even, and certainly it's possible that some places worldwide won't update quickly due to not following caching rules. Usually in the DNS record you set the caching time in seconds and it's typical when you expect changes to set a low value like 300 seconds (5 minutes). Name changes propagate very quickly then. Any root servers are forced to re-check the primary name server after that time.

For your router, I'm not familiar with NetGear, but often this feature is part of the DHCP setup for convenience. If present it would allow adding name-ip pairs. Technically it's done during DNS lookup by intercepting the normal recursion/caching that occurs.

You can run a local DNS server and for ease of setup it need not interface with (global) root servers - it can just do your LAN. Bind is overkill for this but **dnsmasq** is quite light and easy to setup. The setup needed to split DHCP/DNS between the router and dnsmasq is a bit tricky though. Not too hard, but not one step. Personally if this is just for testing and a couple machines I'd just edit the **hosts** file.

---

### Post by MaindotC on 2010-08-31
> **tunist said:**
> ok, I thought it was possible to route a subdomain to another server

I think I've misinformed you.  Now it's all coming back to me.  You can point the subdomain to a different IP and I forget how - it's probably very easy but I'm now just home from work and I'm re-reading what I typed and I don't think I explained it properly.  In fact, this time I actually took 2 seconds of my precious time to [GOOGLE IT](http://www.webhostingtalk.com/showthread.php?t=359352) before talking and I believe it is easily doable.  I apologize for the misinformation because I knew after I hit "submit reply" the last time that something was wrong with what I typed.  Here's an example of my host records on namecheap.com: [IMG]http://a.imageshack.us/img192/7739/screenshothh.png[/IMG]

The asterisk says "point ANYTHING to this ip address", but for some reason I had to specify the subdomains smtp and pop3 otherwise they wouldn't resolve.  According to that post I googled, you can make an entry such as sub.domain.com and assign that an ip address (instead of the domain name as I have done) and make it an A record.  So, I suppose you COULD do that and have the domain.com point to the main web server, and the sub.domain.com point to your server on your network.

> I just looked in my router config (netgear) and it only has dynamic DNS and 'static routes' option, which doesn't seem to be the same as static DNS... perhaps it is, I'll find the manual in a bit.

You shouldn't have to mess with any DNS settings on your router, just forward port 80 to the ip address of the machine running the apache installation (or virtualhost) you want displayed.

I think that may be a little more confusing so let me know if you need me to explain deeper on those instructions.

---

### Post by tunist on 2010-10-18
thanks for the info.. i took a while to reply as i needed to focus on some other issues.. I now have most of my ubuntu issues resolved.. besides the fanspeed on my laptop :).

anyhow..

with this subdomain issue -

I have now registered with dyndns.org which allows a free domain name to be setup that tracks dynamic dns changes on an IP address.. so I can point it to my home IP address.. which is helpful..
the people that manage the shared hosting i am using are pointing a subdomain for my main domain to point to the new dyndns name - so that this new subdomain can dynamically track my home IP address.
so once that's complete my home pc will be accessible via the correct web address..

my only remaining question is 'how would web users be directed to the local sub domains have I have configured on my home pc'?

I already asked this in this thread and the reply was that it must already be configured if it works locally. but there is more to the issue than that.

e.g. I have subdomain1.localhost and subdomain2.localhost setup on my laptop.
presently when webusers visit development.mydomain.com they are sent to 'localhost' on my laptop - the main index page for apache2.. 
how do i configure apache2 to allow visitors to navigate to 'subdomain1.localhost'?

if it were automatic i figured that perhaps users would need to navigate to 'subdomain1.development.mydomain.com' but that's not it.. hehe.

any ideas?

thanks again

---

### Post by BkkBonanza on 2010-10-18
Once users get sent to your system (port#, IP) , regardless of domain name used, it is then up to the **VirtualHost** configuration of Apache as to what directory they end up on your system. VirtualHost allows mapping any names to correct locations for files to be served.

Of course, DNS settings have to be co-ordinated, otherwise public users won't end up at the correct IP and those Apache settings will not be relevant. ie. you need both DNS settings for the subdomain to get users to your IP and VirtualHost settings to direct Apache to the correct files.

BTW the name "localhost" is unusable for public net users. They can only access your system with a public domain/subdomain. DNS settings result in them getting to an **IP** not to a name (like localhost). The purpose of DNS is **name -> IP** translation. Once they are at your IP it is router settings that get them to your system specifically, and then Apache settings that get them to specific files/scripts.

---

