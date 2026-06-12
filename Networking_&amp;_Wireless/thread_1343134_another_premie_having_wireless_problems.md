---
title: "another premie having wireless problems"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by alvinmoneypit on 2009-12-01
Hi,

I'm running 9.04 Ubuntu on a Lenovo N500.  I have a Broadcom STA wireless driver and says it is "currently activated and in use".  I tried using it for the first time this AM at a restaurant.  The connection came up and brought up the restaurants wireless page, but I couldn't navigate to anywhere, saying "no connection present". 

 I tried using the guide at the top of this forum on the 'sticky', but my system says I don't even have an "ndiswrapper" to start with.  

My DSL works fine as far as I can tell and I've done very little with this system since install, just now trying to get it all up and going.  I did go out and get about 268  recommended updates a few days ago.

Thanks for reading, all replies appreciated.

---

### Post by alvinmoneypit on 2009-12-01
bumpinski

---

### Post by Bucky Ball on 2009-12-01
DON'T use ndiswrapper. It is a nightmare and has been superceded for most, if not all, Broadcom cards. Absolutely definitely a completely last resort. Besides, your card is already up and you shouldn't be looking there but at tweaking your settings. 

I suggest you plug in an ethernet cable and get all updates. Go to Synaptic Package Manager (System->Administration) and install ubuntu-restricted-extras.

Go to System->Administration->Hardware Drivers. Is there a driver for your wireless disabled in there? Broadcom B43 Driver?

Go to System->Administration->Network and check your wireless 'properties'. Are all settings correct in there? You are going to need to set that up for the access point you are using.

---

### Post by alvinmoneypit on 2009-12-03
Thanks, Bucky!  

I'm a major newbie to all this fancy linux stuff, but me likey.

I had already got all the auto updates the other day from the update manager automatically.  I didn't try to get them manually from that specific repository as you suggested because I'm on vacation, arrived at my destination, and my wireless works!!!

It's working so great right now, it's even faster than my home DSL running XP.  Many thanks, I'll keep that in mind if I have problems, I don't know why it wouldn't work at the restaurant before.  They told me they had an IT guy, maybe I'll ask him when I get back.

Much love to all readers/ helpers on these forums!!

---

### Post by alvinmoneypit on 2009-12-04
Bucky,

I don't have system>admin>network.  I have system>admin>network tools and system>preferences>network connections and system>preferences>network proxy. 
 If I were to require a password or code to log on, where would I put it?

---

### Post by Bucky Ball on 2009-12-04
Ah, good question. You haven't by any chance installed wicd to try and get your wireless working? That auto-removes the Network Manager. Not sure if the network manager is a default app in 9.04 (I use 8.04) but that is where you would put your locations for wireless (ESSID, security key/passcode) or set up any static IPs you might need. 

Go System->Admin->Synaptic Package Manager and do a search for 'Network Manager'. You will find a few. Install the appropriate one for your setup and 'Network' should then appear in your System->Admin.

---

### Post by alvinmoneypit on 2009-12-04
No, I did not install anything.  I looked at it a bit after I started this thread and then I had to travel.  I did the search as you suggested and I see that I have an appropriate network manager installed.  I can access it from the top right graphic part of the tray.  I can't find where I can access it on the menus though - maybe it's just not there?

Anyway, I have the latest version according to synaptic, it's 0.7.1~rc4.1.
 
 I found where I can enter security code if I have to.  I click the graphic, a window comes up that shows all the radio available out there, below I click "create new wireless network" then the next window has a place for the name and the security code. I would have sent a screen shot, but it won't work with the wireless window opened.

I'm sorry about all the dumb questions - I never used wireless before.

---

### Post by uncaspi on 2009-12-04
network-admin is not installed in 9.04 or 9.10. You have to get it.
sudo apt-get install gnome-network-admin

---

### Post by alvinmoneypit on 2009-12-05
Thanks, but I'm not sure I need it, why would I?

---

### Post by Bucky Ball on 2009-12-05
You have solved your wireless problem? Could you let us know how?

---

### Post by sgosnell on 2009-12-05
My guess is that the restaurant's wireless was down for some reason.  Their 'IT guy' might be one of the waiters, who knows?  Even well-run systems go down now and then, and they can't control their ISP.  I would just ignore that glitch and get on with life.

---

### Post by alvinmoneypit on 2009-12-05
I'm not sure how the problem was resolved, except for the fact that I myself did nothing.

I'm not competent or observant enough to determine if the several reboots and refreshing of the system influenced system parameters enough to corrent anomolies.  

I only tried my wireless 2x, the second time it worked flawlessly, but in a different system.

---

### Post by alvinmoneypit on 2009-12-05
.... that is a different "wireless" system where my hardware and settings remained unchanged.

---

