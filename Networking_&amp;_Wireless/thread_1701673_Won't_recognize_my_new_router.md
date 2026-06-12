---
title: "Won't recognize my new router"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by Hfrog on 2011-03-06
So yeah, I've tried a lot of things to resolve this issue but, nothing seems to work. Here's what I posted on another forum:

> OK NEW PROBLEM

Soo we got a new router, and at the time I wasn't really thinking. 

Probably should have made sure that Ubuntu would know what to do [IMG]http://www.hmotaku.net/forums/images/smilies/bored.gif[/IMG]

Anyway I went to connect and for about 5 minutes it worked fine, faster then before even. However, when my new internet company kicked in Ubuntu would not let me access any internets D:

I think it has something to do with them changing my IP but, not sure how to fix~

So basically what I am saying is HALP

Ok well I am able to input my IP address and Netmask directly into the iPv4 settings menu as a few sites instructed me by using the ifconfig -b command

but when I try and find my gateway address using route -n I get nothing.

Not a single number comes up in any column. What does mean? D:

EDIT: Kind of figuring that it means it can't find my router but, no idea how to solve this.

I've tries reconnecting to it and doing a driver search.

Am I missing something painfully obvious D:

                                                                                   EDITUPDATEDOUBLEPOST: Seems my IPV4 is having issues. I tried both the auto settings and it just cannot find the router. I can find my IP and Mask but, neither me or linux can seem the get teh gate.

Every site I go on for help either gives me stuff I have already tried or is no help :/
Sooo that's my issue. I have a fresh off the disk Ubuntu download because I was forced to reformat. 

Can't really think of any other vital info.

So halp please D:

---

### Post by Hfrog on 2011-03-06
Here are 3 screenshots that may help in figuring out the issue.

[and sorry that they all look pretty much the same, was trying to make them all a little different so I could show as much info as possible]

[http://s73.photobucket.com/albums/i217/harvest_frog/?action=view&current=Screenshot-1.png](http://s73.photobucket.com/albums/i217/harvest_frog/?action=view&current=Screenshot-1.png)

[http://s73.photobucket.com/albums/i217/harvest_frog/?action=view&current=Screenshot-2.png](http://s73.photobucket.com/albums/i217/harvest_frog/?action=view&current=Screenshot-2.png)

[http://s73.photobucket.com/albums/i217/harvest_frog/?action=view&current=Screenshot-3.png](http://s73.photobucket.com/albums/i217/harvest_frog/?action=view&current=Screenshot-3.png)

EDIT: Oh and sorry for double posting.

---

### Post by topcat7736 on 2011-03-07
Hi Hfrog!

I'm not super good with Ubuntu but I'll try to assist you.

If you've installed Ubuntu 10.10, you don't need to modify anything to reach the internet as the Auto eth0 file is already configured for you. Your new router worked initially which proves Ubuntu was configured properly to use it. 

You said when your new internet service kicked in, you could no longer access the internet. I don't know what that means as internet providers don't just "kick in". They must provide a modem either inside a router of their own or as a separate box to which you would connect your router. In either case, when the provider turns on service to your new modem, **the provider must establish a connection between their main office and your modem** before you can access the internet.

You can check local access to your router by loading firefox and going to address "192.168.1.1". Once into the router, you may need a user name & password to access its menus. (Typically ADMIN and ADMIN are used).

If the internet company has established a connection to what they provided you, then unplug from the wall outlet  both the router and modem for 5 minutes and turn off your computer for the same time. Plug back in the modem or router/modem combo and wait for the modem portion to show that it has an internet connection. If it doesn't after a few minutes, you have no internet service from your provider and they need to be contacted to rectify the problem. 

If they gave you a modem and you're using your own router, then after the modem is connected to the internet, plug in your router and wait for it to sync with the main office. You might still need to do a reset on it (typically a reset pin hole or button on the rear of the router) to have it connect properly to the modem.

Once the router & modem have internet access, turn on your computer and you should be able to access the internet without a problem as the Auto eth0 will obtain a new IP address from your router for you.

Al

---

