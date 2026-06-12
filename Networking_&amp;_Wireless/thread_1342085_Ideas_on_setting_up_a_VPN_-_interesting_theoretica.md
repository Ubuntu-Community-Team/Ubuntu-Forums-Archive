---
title: "Ideas on setting up a VPN - interesting theoretical question (with pictures)!"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by Fynn on 2009-11-30
With the growth [DPI]("http://www.theregister.co.uk/2009/11/26/virgin_media_detica/"), and plans by CGHQ to [monitor email and internet use]("http://yro.slashdot.org/article.pl?sid=09/04/27/1428258") maybe now would be a good time to start looking into securing one's internet connection away from those prying eyes...

My setup is currently like this:

[IMG]http://lh3.ggpht.com/_su_S--3zec0/SxP_CAiT09I/AAAAAAAAAlM/7JikypIOsPk/network_diagram.jpg[/IMG]

In addition to being a file and print server the black box (Ubuntu) in the middle of the diagram hosts a small community website and acts as an email server on my cable broadband connection (never switch off the modem, seems to retain it's IP address).

All the devices connect to the internet via the linksys router.

My question is this: would it be feasible to create a VPN between my home server and a rented VPS somewhere, putting a second network card in my home server and then setting the Linksys router to only allow that server access to the internet?  (With the possible exception of the laptop that connects via a different VPN to work, which would continue to go through my router).

What do you think would be the performance implications for VOIP and general internet connectivity?

I would probably use the VPS to host the website and mail server also.

Any ideas as to what software would be required?

Any other thoughts welcome?

Thanks all.

---

### Post by Fynn on 2009-12-06
I've been reading around this subject a little and it appears that my router firmware (Tomato) supports openVPN.

I'm guessing that this could be configured to tunnel web requests through to a vps, but I'm not sure what would be required on the other end.  Can anybody help?  I'm just looking for a high-level overview at this point.

---

