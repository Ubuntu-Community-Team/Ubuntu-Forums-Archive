---
title: "Internet Connection Quirks"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by Baryon on 2006-03-05
Hello - A friend brought over his crashed computer yesterday, and I installed Ubuntu 5.10 (BB) for him. I connected my own Ethernet cable before I installed it, and when it was installed, the Internet worked immediately with zero configuration, which was great.

He took the computer home, and the Internet doesn't work for him. He, too, is using an ADSL modem/router connected to his computer by Ethernet, so I assumed that there would be no difference and that it would work straight away.

He is able to ping an IP address - both his router and Internet domain names will ping with 0% packet loss. I went through the Ethernet troubleshooting topic with him over the 'phone and everything was working - the drivers loaded and so forth. It wasn't a DNS problem etc.

I'm assuming it's a problem with his modem settings. The trouble is, before the computer broke down, it was browsing the Internet fine on Windows 98. So what could possibly be the problem?

(I realise this may be out of the scope of Ubuntu, but I'm stuck for where to turn).

Thanks.

---

### Post by Celestianpower on 2006-03-08
[QUOTE=Baryon]Hello - A friend brought over his crashed computer yesterday, and I installed Ubuntu 5.10 (BB) for him. I connected my own Ethernet cable before I installed it, and when it was installed, the Internet worked immediately with zero configuration, which was great.

He took the computer home, and the Internet doesn't work for him. He, too, is using an ADSL modem/router connected to his computer by Ethernet, so I assumed that there would be no difference and that it would work straight away.

He is able to ping an IP address - both his router and Internet domain names will ping with 0% packet loss. I went through the Ethernet troubleshooting topic with him over the 'phone and everything was working - the drivers loaded and so forth. It wasn't a DNS problem etc.

I'm assuming it's a problem with his modem settings. The trouble is, before the computer broke down, it was browsing the Internet fine on Windows 98. So what could possibly be the problem?

(I realise this may be out of the scope of Ubuntu, but I'm stuck for where to turn).

Thanks.[/QUOTE]

As this is my internet they're talking about, perhaps I should chime in. I figure it must be something to do with the way the router is configured - if anyone has any suggestions of what I could do to fix it, please do say, I'm getting desperate here :(

CP

---

### Post by tyspot on 2006-03-09
mad stab in dark....
ouch hit the wall! try hitting 192.168.1.1 or 192.168.0.1 with a ping and tell us what you get. if it hits something try opening that address in your browser. ex [http://192.168.1.1](http://192.168.1.1)

this may open up your router/Modem page. you will need to either set it up to control the login for auto connect or get the info for your connection and setup the pppoe information in _*deh badger *_with
**sudo pppoeconf**
from the terminal prompt. you will need to enter your admin-user password but that is the same one that you used in the first account you created, unless you or boyfriend or girlfiend or distraught sibling changed it. anyway it will walk you through the process to get the pppoe configured and it will not be a native setup for all houses/accounts. we all have different account info so Dadio's info will need to be entered as he is prompted---- At Baryon's house on his Modem.
Hang in there it will float easy as long as pops has the info or the phone number for ISP support.

If all else fails tell Baryon he shoulda no been browsing on *those *sites! **No computer for a week** and then take care of it on the weekend when you go visit.:twisted: 

Spot Spot I see a Spot.

---

### Post by Celestianpower on 2006-03-09
I got it to work! :D 

I don't know how but I did :)

Thanks all :)

CP

---

