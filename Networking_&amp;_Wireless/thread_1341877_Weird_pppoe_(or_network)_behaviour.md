---
title: "Weird pppoe (or network) behaviour"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by alegallo on 2009-11-30
On my new pc+9.10 64bit I configured my adsl access not to be started automatically, more or less as I did on my old pc 8.04 64bit. 
I have to do so because I have a time-limited access.
I use a D-Link DSL302T Ethernet modem/router and it looked like everything was working, until I restarted. 

After that "pon" and "poff" did not work anymore.

I tried to repeat "sudo pppoeconf" to check about typing mistakes, but I stopped it because I wanted to take a backup copy of my "dsl-provider" file, and "pon" started working again.

After several tries I still must launch "sudo pppoeconf" to access the internet. It does not matter if I break it before overwriting the previous configuration file, it just works after launching pppoeconf.
Once I run it it works all the session long, so I can log in and out any time I want, but on restart it does exactly as before.

I think that the problem lies in the network, because the connection starts as soon as pppoeconf searches for an "access concentrator" (sorry, I use Ubuntu in Italian, so I guess it should be the English term for what I see).
Well, I rather think that the connection starts as soon as it finds some ethernet card or the modem, but I'm not so experienced in Ubuntu to understand what's happening.

Any idea of what may be wrong? :confused:
Every help or advice is welcome ;)

---

### Post by alegallo on 2009-12-01
no idea? really no hint? :(

---

