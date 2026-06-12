---
title: "Router Host File?"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by hithisisatempaccount1532 on 2010-02-23
I was pondering over whether or not Linksys routers ship with a host file in it...if it doesn't, can you just manually add one via an FTP transmission?
:confused:
It would be extremely helpful.

---

### Post by doas777 on 2010-02-23
many routers these days can operate a dns zone, so perhaps that will work for you.

---

### Post by hithisisatempaccount1532 on 2010-02-23
> **doas777 said:**
> many routers these days can operate a dns zone, so perhaps that will work for you.
Please elaborate on what a DNS Zone is... I'd like to learn how to do this and globally add a hosts configuration versus having to use one for each PC on a network.

---

### Post by pirateghost on 2010-02-23
> **hithisisatempaccount1532 said:**
> Please elaborate on what a DNS Zone is... I'd like to learn how to do this and globally add a hosts configuration versus having to use one for each PC on a network.
Thats what a DNS zone does.  you just answered yourself.

i would suggest you look at the manual for your particular model router, or find some info on the internet.  one cant answer a question as vague as you have requested without knowing some things first, mainly the model of the router you have

---

### Post by hithisisatempaccount1532 on 2010-02-23
> **pirateghost said:**
> Thats what a DNS zone does.  you just answered yourself.

i would suggest you look at the manual for your particular model router, or find some info on the internet.  one cant answer a question as vague as you have requested without knowing some things first, mainly the model of the router you have
Alright, I will research it up, thanks for the feedback!

---

### Post by hithisisatempaccount1532 on 2010-02-23
The only thing I managed to find in relation to it is just the standard DNS blocking forms incorporated in the Linksys default router firmware which doesn't suit my needs... I'd like to import a massive host file list into the routers DNS blocking area.

---

### Post by pirateghost on 2010-02-23
> **hithisisatempaccount1532 said:**
> The only thing I managed to find in relation to it is just the standard DNS blocking forms incorporated in the Linksys default router firmware which doesn't suit my needs... I'd like to import a massive host file list into the routers DNS blocking area.
you want to block hosts?

can you explain what goal you are trying to achieve here, instead of giving us bits and pieces of the puzzle?  that would help out immensely.  from your first couple of posts it sounds like you want a DNS server to be able to hand out IP addresses when you request a name in your LAN, which is a local DNS servers job.

then from this last post it sounds like you are trying to BLOCK access to certain domains from the LAN.  if this is the case you can easily get a free account on opendns.com and configure your blocks there, then make your router point to the opendns servers for DNS, and all your clients point to the router for DNS.  the router then acts as a DNS forwarder, forwarding all name requests to OPENDNS servers.

what model router is it?  perhaps you can flash it with dd-wrt firmware or tomato firmware and get the desired result.

---

### Post by hithisisatempaccount1532 on 2010-02-23
I'm sorry for the cofusion... I wanted to make a HOSTS file type thing on my router which would block websites... ie: 127.0.0.1 x.y.z

Router is a WRT160NL

---

### Post by pirateghost on 2010-02-23
> **hithisisatempaccount1532 said:**
> I'm sorry for the cofusion... I wanted to make a HOSTS file type thing on my router which would block websites... ie: 127.0.0.1 x.y.z

Router is a WRT160NL
in that case, have a look at an account on OpenDNS.com.

other options beside that include:
set up your own DNS server and add your blocks to it
set up a firewall/router using linux or a specifically designed distro (pfsense, vyatta, smoothwall, etc)
or manually replicate all the blocklists out to all the clients.  (this process could be semi-automated via scripting and rsync)

anyone else got any other ideas?

---

### Post by hithisisatempaccount1532 on 2010-02-23
I already knew of OpenDNS except it limits the amount that can be blocked.

---

### Post by pirateghost on 2010-02-23
> **hithisisatempaccount1532 said:**
> I already knew of OpenDNS except it limits the amount that can be blocked.
have you used the categories instead of individual blocks?

---

### Post by hithisisatempaccount1532 on 2010-02-23
Well yes, but I want to block particular ad/tracking websites that are extremely common around the internet.

IE... Google Analytics on this website.

---

### Post by doas777 on 2010-02-23
its sounding like you need a host router, rather than an appliance like a lynksys.

---

### Post by 2hot6ft2 on 2010-02-23
You might be able to put dd-wrt on it depending on what version the router is then you'll have iptables and lots of features like site blocking.

[http://www.dd-wrt.com/site/support/router-database](http://www.dd-wrt.com/site/support/router-database)

---

### Post by hithisisatempaccount1532 on 2010-02-24
Well I know about the individual blocking of websites, the standard Linksys firmware has that feature but I want to add in hundreds, if not thousands, of websites for the router to ignore and put on loopback or deny the DNS request from sending/recieving.

Once again, thanks for the feedback.

---

### Post by 2hot6ft2 on 2010-02-24
> **hithisisatempaccount1532 said:**
> Well I know about the individual blocking of websites, the standard Linksys firmware has that feature but I want to add in hundreds, if not thousands, of websites for the router to ignore and put on loopback or deny the DNS request from sending/recieving.

Once again, thanks for the feedback.
You can block by
1. Days
2. Times
3. Services (Catch all P2P Protocols)
4. Website Blocking by URL Address
5. Website Blocking by Keyword

Maybe blocking by keyword would work for what you have in mind.
Or a custom firewall using iptables or a script.

---

### Post by pirateghost on 2010-02-24
If you truly need that kind of control (thousands of websites???), i would suggest moving away from a simple Stinksys router and set up a real Firewall/Router and use the Stinksys as just an access point.  

have a look at a firewall/router distro for this purpose, something that can utilize squid+dansguardian preferably (smoothwall has great integration with this) or maybe pfsense.  your requirements are kind of extensive.  what kind of network are you trying to protect and filter?

---

### Post by hithisisatempaccount1532 on 2010-02-24
I will look into firewall setups, thank you.

One final question and then all of my inquires will be resolved:

With the keyword blocking... if I simply put in "ad" as a keyword, would it block things like quantserve and things of the sort? (Google Ads, AdMob, etc, etc...)

---

### Post by 2hot6ft2 on 2010-02-25
> **hithisisatempaccount1532 said:**
> I will look into firewall setups, thank you.

One final question and then all of my inquires will be resolved:

With the keyword blocking... if I simply put in "ad" as a keyword, would it block things like quantserve and things of the sort? (Google Ads, AdMob, etc, etc...)
I honestly don't know if it would or not but I suspect it would block everything with "ad" in it like you say "(Google Ads, AdMob, etc, etc...)".

I would think that could create some problems in that case blocking something as small as 2 letters that could be in so many things other than ads like "launchpad" for one example. I can see what you're after now and I think that the idea pirateghost gave may be more what you're after.

It can be done. I'm just not familiar with doing it but I'm sure there are many here that are.

---

### Post by pirateghost on 2010-02-25
> **hithisisatempaccount1532 said:**
> I will look into firewall  setups, thank you.

One final question and then all of my inquires will be resolved:

With the keyword blocking... if I simply put in "ad" as a keyword, would  it block things like quantserve and things of the sort? (Google Ads,  AdMob, etc, etc...)

OpenDNS offers categories that it will block for you, so you dont have to input all those websites.  One of those categories is ADS and another is PORN.  have a look at all the categories they can block for you and then figure out if you truly need to add your own 'thousands of websites' list.

blocking a keyword like ad is going to cause a lot of issues.  places like opendns provide categories so you dont have to maintain lists of websites to blacklist.  have a look at it before you blow it off, it might just provide exactly what you are looking for.

---

### Post by nullvariable on 2010-02-25
OpenDNS also raises their limits very high for sites you can block if you are willing to pay $10/year (which is totally worth it). I would echo the other posters suggestion of using OpenDNS because ad companies change their servers on a very regular basis (because of people blocking them). Your list will become very bloated and out of control if you try to maintain it yourself. Using a service like OpenDNS will block this stuff network wide for you and keep you from having to maintain a massive list with tons of dead servers.

> **pirateghost said:**
> OpenDNS offers categories that it will block for you, so you dont have to input all those websites.  One of those categories is ADS and another is PORN.  have a look at all the categories they can block for you and then figure out if you truly need to add your own 'thousands of websites' list.

blocking a keyword like ad is going to cause a lot of issues.  places like opendns provide categories so you dont have to maintain lists of websites to blacklist.  have a look at it before you blow it off, it might just provide exactly what you are looking for.

---

### Post by hithisisatempaccount1532 on 2010-02-25
Well, now the only thing lacking is the DDNS feature shipped on Linksys routers doesn't include OpenDNS on their list, kinda a pain in the butt. I suppose I'll go back to trying OpenDNS, I've been using Google's DNS servers and have been satisfied with the speed but I prefer features over speed personally.

Once again, thank you everyone whom has given support, it is GREATLY obliged.
 :KS

---

### Post by 2hot6ft2 on 2010-02-25
> **hithisisatempaccount1532 said:**
> Well, now the only thing lacking is the DDNS feature shipped on Linksys routers doesn't include OpenDNS on their list, kinda a pain in the butt. I suppose I'll go back to trying OpenDNS, I've been using Google's DNS servers and have been satisfied with the speed but I prefer features over speed personally.

Once again, thank you everyone whom has given support, it is GREATLY obliged.
 :KS
That brings you back to dd-wrt which on a linksys router has the DDNS ability.

---

### Post by pirateghost on 2010-02-25
> **2hot6ft2 said:**
> That brings you back to dd-wrt which on a linksys router has the DDNS ability.
the stock firmware has DDNS as well.  he was referring to wanting OPENDNS as an option in the router.

---

### Post by 2hot6ft2 on 2010-02-25
> **pirateghost said:**
> the stock firmware has DDNS as well.  he was referring to wanting OPENDNS as an option in the router.
Does it have the "Custom" option under DDNS?

---

### Post by pirateghost on 2010-02-25
> **2hot6ft2 said:**
> Does it have the "Custom" option under DDNS?
doubtful, but can you even set up OpenDNS to update using it?

i have a wrt54g-tm flashed with dd-wrt-mega, but it is only being used as an access point.  i use vyatta for my router/firewall

---

### Post by 2hot6ft2 on 2010-02-25
> **pirateghost said:**
> doubtful, but can you even set up OpenDNS to update using it?

i have a wrt54g-tm flashed with dd-wrt-mega, but it is only being used as an access point.  i use vyatta for my router/firewall
I don't know since I haven't played with the Custom option but if it can use all those others then it's an option until it's ruled out. I am using the DDNS function on my wrt150n so I'm not going to play with it and mess things up. It's working too good to throw a wrench in it now.

---

### Post by hithisisatempaccount1532 on 2010-02-25
It is indeed, very easy to setup OpenDNS updates via the 'Custom DDNS' option on a WRT-DD router. I've found it easier to simply deploy a simply local HTML file that has an embedded script to auto-send the login credentials through an encrypted SSL and tell OpenDNS I want to update my IP-Address which seems to have solved my issue. Now when I change my IP address all I do is simply double click. :)

---

### Post by 2hot6ft2 on 2010-03-01
> **hithisisatempaccount1532 said:**
> It is indeed, very easy to setup OpenDNS updates via the 'Custom DDNS' option on a WRT-DD router. I've found it easier to simply deploy a simply local HTML file that has an embedded script to auto-send the login credentials through an encrypted SSL and tell OpenDNS I want to update my IP-Address which seems to have solved my issue. Now when I change my IP address all I do is simply double click. :)
Glad you got things set up the way you were wanting. I just came across something in synaptic that might have fit your needs and thought I would let you know.

It's called DansGuardian
> DansGuardian filters the content of pages based on many methods
including phrase matching, PICS filtering and URL filtering. It does
not purely filter based on a banned list of sites.

It provides real-time virus scanning capabilities for content access.

DansGuardian is designed to be completely flexible and allows you to tailor
the filtering to your exact needs. It can be as draconian or as
unobstructive as you want. The default settings are geared towards what a
primary school might want but DansGuardian puts you in control of what you
want to block.

DansGuardian requires squid or another similar caching proxy server
on your local network.


---

### Post by hithisisatempaccount1532 on 2010-03-02
Excellent, thanks!

I think I've sorted things out...

I've made a client bridge DD-WRT router, having it use DDNS updated for OpenDNS' servers to update that ban list of URL's and then I've also got a startup script that downloads a hosts file full of lovely url's to return to localhost for my network. 

Once again, thanks and all help was greatly appreciated. My next project will be either making or buying a firewall probably. ^_^

Thanks, very much to all of you.

---

