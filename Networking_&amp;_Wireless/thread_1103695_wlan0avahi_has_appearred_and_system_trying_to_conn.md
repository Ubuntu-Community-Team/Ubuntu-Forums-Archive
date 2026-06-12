---
title: "wlan0:avahi has appearred and system trying to connect with it."
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2009-03-22
Hi all,

Was playing around trying to get networking happening with my three machines a few days ago. I was attempting to set a static IP on the laptop. I did this on the D-link 704P router but that didn't seem to work, so I changed the ip on the machine. All's well with the two wired machine, but my laptop, which is the one I was working from, seems to have developed a new interface (interesting concept as I draw toward mid-life!).

It is trying to use the new interface 'wlan0:avahi' instead of the regular 'wlan0'. Consequently, not setup to my access point, not getting served dhcp by the router and a million miles from connection. If anyone knows how to delete it, which is what I have been researching, that would be great. 

I usually leave this kind of tweaking until the holidays for this very reason, but I need this machine to be up kinda desperately for uni, so if anyone has any suggestions they would be gratefully received ... ;)

---

### Post by Bucky Ball on 2009-03-23
After further investigation, I think there is something going on with one of the routers perhaps.

Here's the setup: I have two computers wired to a D-Link 704P which has four ports and a print server.

I have the laptop wireless connecting with another four port/wireless D-Link router (DI-524 I think, Air-G) which I have plugged into the 704P. So laptop to DI-524 through ethernet cable to port on the 704P (through 704P print server to printer as required).

 All has been working fine for over a year with this setup. The wireless connection is the only one that is a problem so I am guessing it is between the laptop and the wireless router.

I have checked the wireless router and the dhcp serving is set to 'disabled'. Do I need this set to 'enabled' for the 704P to serve an IP through the 524? It was set this way but I thought both routers might have been trying to serve the laptop. I changed it and no different.

I have a feeling maybe I changed something on the wrong router when I was trying to setup networking (I thought I was working only on the 704P only but I may have logged into the other by mistake; both same IP). 

The appearance of the 'wlan0:avahi' interface still has me bamboozled. There goes three hours of note writing I need to do for uni tomorrow. That's computing.

Any help?

---

### Post by Bucky Ball on 2009-03-24
Okay, 'wlan0:avahi' has gone. Now the laptop won't connect with anything. I plug into the 704P with an ethernet cable and doesn't pick that up either. I plug into the 524 with ethernet, can't log in to admin screen to change any setting on the router. Stuck. Both wired machines working fine through the 704P. I am about to try one of the wired machines through the 524 to see if the 704P serves it an address. This will rule out the routers and then I will know this is the laptop. Been meaning to reinstall for awhile, preferably during the holidays, but this may force my hand. 

It's about that time ...

Help!!! If you have any ideas, gratefully appreciated. :)

---

