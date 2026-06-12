---
title: "comcast business, web server, and a WRT54G"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by revenant138 on 2009-07-20
Hey all,

I just upgraded to comcast business so I don't violate TOS by having a web server. 

Before, I had my comcast residential modem plugged into a WRT54G and used the router to update dyndns.org with my dynamic IP info. No changes had to be made to the modem for that to work. 

When I changed to a business acct, my site isn't working any more. My WRT54G reports the IP address as 10.1.10.x so I know the modem isn't passing me the public IP after the change. I got into the modem and looked for settings that would forward the IP and I don't see anything. 

I think I might be stuck paying for a static IP, but I wanted to check here first. Any ideas?

I thought I could maybe connect th' server straight to the modem and use a script to update dyndns instead. 

My modem is a SMC 8014

Thanks in advance for any help <3

---

### Post by slavik on 2009-07-21
[www.whatismyip.com](www.whatismyip.com) should tell you your IP.

---

### Post by revenant138 on 2009-07-21
I already know my IP is not static, I am wondering if I can make dynamic IP work with my modem and router, or if I have to add static IP service.

---

### Post by superprash2003 on 2009-07-22
your WAN IP can be dynamic , but your LAN IP needs to be static so that you will be able to open ports properly.

---

### Post by revenant138 on 2009-07-22
Any guess how I can do that? I went into the modem's settings before and didn't see anything that was much help.

Thx for the replies :)

---

### Post by darco on 2009-07-22
What version is the Linksys? If you have one between 1 thru 4, I would consider updating your firmware to a 3rd party like Tomato (which I use). You will have alot more functions for your web server. I use static IP's for my pc's but pay for dynamic.
Check out this link..scroll down for the Tomato forum or which ever 3rd party firmware you decide

[http://www.linksysinfo.org/forums/?](http://www.linksysinfo.org/forums/?)

darco

---

### Post by superprash2003 on 2009-07-23
you needn't worry about WAN , cause dynamic or static would work.. but for LAN , static is required and for that you need to make changes in ubuntu and not your modem.. have you tried opening ports in your modem? 

here's a guide on setting up static ip [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by revenant138 on 2009-07-25
Hey er-body :) I figured it out - I'm just using ddclient with settings to go to dyndns and ask what my ip is then update it with that. Works great, with one problem - I can't see my website from my home network, not sure why that is yet. Can't see it even if I enter my public IP in the url.

---

### Post by revenant138 on 2009-07-25
OH hey - if I just use the private IP for my own computer (which hosts the site) I can see it from within my network. Good enough for me :popcorn:

---

