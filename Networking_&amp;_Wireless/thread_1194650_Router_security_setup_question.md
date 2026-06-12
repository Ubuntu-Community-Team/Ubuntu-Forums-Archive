---
title: "Router security setup question"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by timzak on 2009-06-22
I have a Linksys WRT54GL router.  Looking through all the setup options in the router configuration pages, I'm wondering if there are some non-default settings I should be playing with to increase security.  Such as MAC address filtering, IP filtering.  If I put my network machines in here, does it increase security by only allowing those MAC/IP's in?  If I prevent the wifi from broadcasting, does that help?  Are there other settings I should be aware of?  Or do the default settings pretty much do the job?

Thanks,
Tim

---

### Post by t0mppa on 2009-06-22
In my biased opinion, just setting up WPA2 with a strong password will make your network secure enough to make breaking it so troublesome that it's easier to try and breach your neighbours wireless (which likely has lesser security) instead.

MAC addresses can be changed and if you enable MAC filtering, you'll have to change the router configuration every time a friend drops by with a laptop and the SSID can be found out even when it's not actively broadcasting it.

If you really want to make it hard to use for outsiders, much better options are scaling the transmission power down, so it can only be caught from inside your appartment and switching the modem off when you don't use it, which will also save you some cash on the electricity bill.

---

### Post by timzak on 2009-06-23
Thanks.  I haven't ever had a friend come over to connect to my wireless.  Just my family's computers.  I don't really envision having people coming over to use my wireless, so that's not an issue.  In that case, is MAC filtering helping any more than if it was disabled?

I didn't realize you could scale the transmitting power down.  What is such a setting called?

---

### Post by jhannah on 2009-06-23
As t0mppa said, it's usually sufficient to choose a unique SSID and a decent password (8+ alpha numeric mixed case with at least one or two special characters- you can always use pwgen to make one). It's important to pick a unique SSID for your wireless access point as this value is used in conjunction with the password in WPA. This makes it more difficult to pre-generate large tables that enumerate all the possible passwords (see [http://www.renderlab.net/projects/WPA-tables](http://www.renderlab.net/projects/WPA-tables) for a lot more information on that).

It will always be a trade off but unless you have someone seriously dedicated to accessing your wireless network, the above should really keep your network secure.

---

### Post by timzak on 2009-06-24
Thank you both.  Sounds like I'm in good shape then.  I already have a unique SSID and strong password.  Just wondering about the MAC filtering...if it was any help, or perhaps if it was something that is bad to do.  Sounds like it doesn't hurt, and may help against inexperienced hackers...

---

### Post by cariboo on 2009-06-24
MAC filtering really doesn't work, as it is pretty easy to clone it with the proper tools.

---

