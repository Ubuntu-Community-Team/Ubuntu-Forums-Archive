---
title: "Can't get on Internet via wireless"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by minimustangs on 2009-07-30
Just installed Ubuntu 8.10 on an Acer Travelmate 5100 laptop. Last time I tried this on a laptop everything went horribly wrong. LOL.

Seems that virtually everything is working as it should - except my brain. Must be from years of exposure to M$ O/S'es.

Anyways...

I can connect to my network and initiate a login to my DSL provider, as long as I'm wired. As soon as I unplug the cable I can't get on the internet, although I can print to my network printer, so I know my wireless card is actually working. When I need to figure out is how to activate a DSL connection while I'm unplugged from the router.

My network gear is a Dlink DSS-8+ switch, Dlink WBR 1310 rounter/wireless and a Zhone DSL modem

Thanks for the read

Steve

---

### Post by imapostdoc on 2009-08-31
Hi Steve,
we seem to have a similar (or even the same) problem. I can detect my own network, but not connect to it.
Did you make any progress since your post?
Cheers,
Peter

---

### Post by jwrede on 2009-08-31
Peter, sounds like problem is different, as you see the network but aren't able to connect (and obtain an IP).  Are you running wireless security (e.g. - WEP, WPA) on your router?  If you are, can you connect if you turn the security off?

Steve, I'm a little confused about what you mean by "initiate a login to my DSL provider" - as that should be handled by your router / switch and not the individual PC.  I don't know how you have your network set up, but it sounds like the router is not seeing the internet, so I would start with the router "WAN" configuration.

---

### Post by imapostdoc on 2009-09-01
Dear jwrede,

thanks for the reply. Actually, things got even worse. While the network light still comes up blue, I cannot detect any networks anymore. It took me several attempts to install ndiswrapper a year ago, but then it worked for the past year. Do I have to do that again?

Before that happened, my wife tried to disable the network security (WEP), but had no more success. I posted some diagnostic data in another thread "problem with wireless router D-link WBR 1310, Ubuntu 8.04 ".

I'm at the office now, but will be back with the laptop at home in the evening. 

Best regards,
Peter

---

### Post by imapostdoc on 2009-09-09
Hello jwrede,

if you are still willing to help me, I managed to get ndiswrapper working again. Now I'm still stuck on hooking up to my own network. I have a 24 letter hexadecimal WEP password and a friend had no trouble to connect his Mac using this password. Why can't I do the same? Are there any diagnostic commands that might help?

Thank you and best regards,
     Peter

---

