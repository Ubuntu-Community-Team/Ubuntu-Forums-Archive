---
title: "Sharing two pcs for DSL connection"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by tech291083 on 2011-07-31
Hi,

I have two pcs. One is a laptop with Windows XP and another is a desktop with Ubuntu 10.10. Until today laptop was getting connected to the DSL connection with no problems at all. But today only when I connected my Ubuntu desktop to the net that too for the first and then connected the laptop using the same cat 5 cable supplied by the isp there is no internet connection on my laptop any more and the error is -** Error 691: *Access was denied because the username* and/or *password was invalid on the domain*.**

How is this possible? Only few minutes ago laptop was getting internet with no problem at all. Please help, thanks

---

### Post by dandnsmith on 2011-07-31
Would you like to provide some more detail - I cannot see that you've described your networking setup.
Do you have a router? if not, what means of connecting to the internet?
How are the machines set - to use DHCP?

---

### Post by tech291083 on 2011-07-31
> **dandnsmith said:**
> Would you like to provide some more detail - I cannot see that you've described your networking setup.
Do you have a router? if not, what means of connecting to the internet?
How are the machines set - to use DHCP?


Sorry, for the description.

I do not have a router or modem. Just a cable cat 5e comes directly into my home from a switch provided by my isp on the top floor of the building where I live and I just plug it into my Ethernet port and it works with a user name and password. It is a DSL connection. Yes the machines use DHCP. This is a silly problem as it looks to me, otherwise why the same laptop that was just working fine suddenly stopped connecting to the net. While the other does very well. Not sure this is MAC binding issue as my isp has clearly denied doing it. Thanks

---

### Post by jamespaul.32187 on 2011-07-31
Sharing two PCs for DSL connection is a nightmare process.. instead you can try through wired..

---

### Post by dandnsmith on 2011-07-31
OK, so the nub of the matter is exactly what is this connection provided by an ethernet from a switch on the top floor.
It's possible that what you are doing is connecting to a port, and there is an IP address supplied with a lease. This then persists when you change to the other laptop, but the IP issuer denies the fresh connection (to a recognisably different MAC) - the error message doesn't sound obviously right for that, but it may still be what is happening.
A workaround might be to install your own IP access point (but Im not sure how the 'supplier' would deal with this), or possibly use ICS (Internet Connection Sharing) with one of the laptops as the principal connection and the other as slave.
Any chance of getting a second connection from the top floor?

---

### Post by tech291083 on 2011-08-01
> **dandnsmith said:**
> the IP issuer denies the fresh connection (to a recognisably different MAC) 
A workaround might be to install your own IP access point (but Im not sure how the 'supplier' would deal with this), or possibly use ICS (Internet Connection Sharing) with one of the laptops as the principal connection and the other as slave.
Any chance of getting a second connection from the top floor?

Hi,

Yes you are right. I just talked to my ISP and he says that they do MAC binding so not allowing any other pc obviously with a different MAC to connect using the same username and password. 

He then suggested me to use a wireless router and then connect both the pcs (laptop and desktop) to the router itself. Unfortunately the laptop does not have a wireless port (It is a bit old, but hardly used and works well) and the desktop does have a wireless port either. 

You have mentioned that a possible workaround might be to install your own IP access point. Do you mean a router? But I need one which is not wireless. 

Also you have mentioned the ICS (Internet Connection Sharing) with one of the pcs as the principal connection and the other as slave. Any suggestions as how I can do so?

There is no chance of a second connection.

 Thanks.

---

### Post by tech291083 on 2011-08-01
My ISP is happy to allow me to use a router  (access point in your words, I guess). So how to go about making a wired router connect to these two pcs - a laptop with Windows XP and a desktop with Ubuntu 10.10? Thanks

---

### Post by dandnsmith on 2011-08-03
That is the easy option - just set each of them to use DHCP (they do this by default, anyway) or you can use fixed IP addresses within the range the router services. The router gets set to pick up IP address etc from your ISP, the PCs get their addresses from the router, which handles the traffic routing needed by the 2 PCs.

Choice of router - up to you, but I'd go for something like a Netgear DG834 (which has 4 ethernet ports).

We, as an advisory group can help if you're uncertain whether a particular router can be used.

---

### Post by tech291083 on 2011-08-03
Differnet OS on both pcs should not be a problem, I guess, thanks

---

### Post by dineshs on 2011-08-04
I think the following setup will work if your desktop PC has 2 ethernet cards.
Connect eth0(desktop) to the switch on top floor.
Run [COLOR="Blue"]sudo pppoeconf eth0[/COLOR] and configure your DSL connection.(You can connect DSL using [COLOR="Blue"]pon dsl-provider[/COLOR])
Connect eth1(desktop) to the laptop and configure eth1 via network manager for ICS ie shared to other computers option under ipv4 tab.
On laptop configure LAN manually as explained [here]("http://ubuntuforums.org/showpost.php?p=10134498&postcount=2")

---

### Post by dandnsmith on 2011-08-04
> **dineshs said:**
> I think the following setup will work if your desktop PC has 2 ethernet cards.
Connect eth0(desktop) to the switch on top floor.
Run [COLOR="Blue"]sudo pppoeconf eth0[/COLOR] and configure your DSL connection.(You can connect DSL using [COLOR="Blue"]pon dsl-provider[/COLOR])
Connect eth1(desktop) to the laptop and configure eth1 via network manager for ICS ie shared to other computers option under ipv4 tab.
On laptop configure LAN manually as explained [here]("http://ubuntuforums.org/showpost.php?p=10134498&postcount=2")

I think you must have got the threads confused - nowhere has 2 ethernet cards been mentioned, and there is a solution just needing a router (suggestion from ISP)

---

### Post by tech291083 on 2011-08-05
> **dandnsmith said:**
> I think you must have got the threads confused - nowhere has 2 ethernet cards been mentioned, and there is a solution just needing a router (suggestion from ISP)

Yes, right, my only solution is a router now. Thanks a lot.

---

