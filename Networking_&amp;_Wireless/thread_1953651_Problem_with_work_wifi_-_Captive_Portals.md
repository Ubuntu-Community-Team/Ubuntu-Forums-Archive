---
title: "Problem with work wifi - Captive Portals?"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by HawkST on 2012-04-06
I have an old laptop running 8.04 HH and the wireless is sorted and appears to work fine from my home network, connects to wifi, connects to internet, not a problem.

At work however, it connects to the wifi and the network manager shows it as connected to the wifi, however it doesn't appear to connect to the internet (the girl sitting next to me could connect to the internet fine via the wifi). Ping doesn't work and firefox doesn't connect to any sites.

The wifi at work has a captive portal that I need to go past before I can connect to the internet but this doesn't appear to show up, either on FF or on IE in a VirtualBox Windows XP.

Are there any issues with captive portals and Ubuntu?
Or is there another potential reason for this?

---

### Post by Ms. Daisy on 2012-04-09
Is there a reason you're running such an old version of Ubuntu?  [Ubuntu stopped supporting]("https://wiki.ubuntu.com/Releases") 8.04 last year.

I would encourage you to consider switching to something that is still supported. 

If you're determined to stick with 8.04, then burn some live CDs of some light distros (xubuntu, lubuntu, mint, etc.) and see if you can connect at work using them.  

I would highly encourage you to talk to the network managers at your work to see what they say. If it were my corporate network, I wouldn't want old, unsupported operating systems connecting because of the security risk, so perhaps they have something blocking you in that regard.

---

### Post by HawkST on 2012-04-11
> **Ms. Daisy said:**
> Is there a reason you're running such an old version of Ubuntu?  [Ubuntu stopped supporting]("https://wiki.ubuntu.com/Releases") 8.04 last year.

I would encourage you to consider switching to something that is still supported. 

If you're determined to stick with 8.04, then burn some live CDs of some light distros (xubuntu, lubuntu, mint, etc.) and see if you can connect at work using them.  

I would highly encourage you to talk to the network managers at your work to see what they say. If it were my corporate network, I wouldn't want old, unsupported operating systems connecting because of the security risk, so perhaps they have something blocking you in that regard.

Hey, thanks for replying!

Yes, I am aware Ubuntu stopped supporting 8.04 a while back. It is a pretty old laptop (circa 2006) and I'm mildy concerned about upgrading as there are a lot of documents etc. and I don't know if the laptop could handle it! (is there a big hardware requirements difference between 8.04 and the next LTS?).
I can't speak to someone at the office as it was set up by our IT dept who are not on-site, in fact being an Ubuntu user I'm pretty much top of the food chain in terms of in-house IT!

If someone using another computer tries to connect to the internet without using a browser and going through the captive portal first, they get error messages that would appear to indicate they are not connected to the internet. Once they load up a browser and try to connect to a website, the captive portal loads and all is forgiven. 
For some reason on my computer though it's not bumping me to the portal when I use a browser, and just seems to think I'm offline.

---

### Post by Ms. Daisy on 2012-04-11
It sounds like a problem with the captive portal, and I don't know anything about those (beyond that they exist).

You're sure that the guys that set up the captive portal can't help you connect with it?  It seems odd that they would have it but not be able to help anyone with it.

---

### Post by HawkST on 2012-04-13
Yea afraid not, they do IT support for the whole company and any kind of reasonably low-level IT problem like this is going to be "use Windows" as far as help goes - they do have bigger fish to fry with troubleshooting.
I'll just have to try and figure it out myself - I'll report back if I figure out what happened for anyone who comes across this thread with a similar problem in about 3 years!

---

