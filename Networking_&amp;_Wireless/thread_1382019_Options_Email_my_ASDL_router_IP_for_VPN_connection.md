---
title: "Options: Email my ASDL router IP for VPN connection"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by fisheater on 2010-01-15
Email my ASDL router IP for VPN connection

Hi all,

My adventure with NX nomachine continues with great success. Thanks for all you input and suggestions &#8211; I am still polishing the project but it has been straight forward to date.

One questions I have is how to stay current with my ASDL router's IP. I use a Canadian provider with a dynamic IP that is constant for days at a time. Without powering my router down or any power outages, my IP will change. With that IP change, I am unable to login to my desktop.

One windows style program I found does the job ([http://download.cnet.com/IP-Discoverer/3000-2381_4-10253532.html](http://download.cnet.com/IP-Discoverer/3000-2381_4-10253532.html)). It emails my current IP to a predefined email. I am unable to  seem to find one for linux.

Ideally I would have a ubuntu program on my desktop (NX server) that would keep me up to date on my IP via email so I can login.

Anyone have any experience with that? Or have any other suggestions on how to do this (I dont know the best way to keep that IP up to date besides requesting a static IP from my provider).

Also, I use a DD-WRT router, can it send me an update to my new IP address?

TY

FE

---

### Post by changingstate on 2010-01-15
Hiya fisheater.

To keep track of my own external IP, I use a dynamic domain name from dyndns.org. There are other services, but this is the one I've used for years. There's some  information on their site about some linux based clients to help keep them updated about your IP address here : [http://www.dyndns.com/support/clients/](http://www.dyndns.com/support/clients/)

As you mention you use dd-wrt, you might lke to note one of the clients mentioned on that last page has a tutorial page on the dd-wrt wiki : [http://www.dd-wrt.com/wiki/index.php/Tutorials](http://www.dd-wrt.com/wiki/index.php/Tutorials)

This service will basically allow you to use a domain name ( fisheater.dyndns.org, say ) rather than your IP address when it's up and working. Very, very useful if you want to run servers economically.

---

### Post by fisheater on 2010-01-15
Thanks for the info!

Your info put me on the right track – I didn't know what I was looking for (or how to search for what I was after). Your suggestions helped me find the info.

Set up:
DDWRT router: 
- Setup -> DDNS -> dyndns.org -> (login info + hostname)
from: ([http://www.no-ip.com/support/guides/routers/dynamic-dns-on-dd-wrt.html](http://www.no-ip.com/support/guides/routers/dynamic-dns-on-dd-wrt.html))

NX nomachine login:
General tab -> host mysite.dyndns.org
Username + Password
from: ([http://www.dd-wrt.com/wiki/index.php/DDNS_-_How_to_setup_Custom_DDNS_settings_using_embedded_inadyn_-_HOWTO](http://www.dd-wrt.com/wiki/index.php/DDNS_-_How_to_setup_Custom_DDNS_settings_using_embedded_inadyn_-_HOWTO))

Login success!

This looks great and if I understand what is happening...
1.My router communicates with dyndns and updates my current IP.
2.When logging on to mysite.dyndns.org I am redirected to my current IP.

Is there any risk of man in the middle type of attack going through this type of server?

Thanks again this one is solved! Hope it helps another user.

FE

---

### Post by changingstate on 2010-01-15
Yep, you've got the idea. It is possible to man in the middle someone using this service, if the attacker gets your authentication details ( you've got to log in to update the IP ).

---

### Post by fisheater on 2010-01-15
Hmm,

Just so I understand this fully...

My router talks to DynDNS.org and updates when my ISP changes my IP.

When I log in to my NX session, it goes via the dyndns.org which then redirects my request to my new/updated IP.

I will not have to enter a new IP, just keep my acct.dyndns.org in the hosts field?

If that is the case, that is a crazy good service.

TY

FE

---

### Post by changingstate on 2010-01-15
Spot on, you've got it exactly. I'm glad you like it. :)

---

