---
title: "zte mf112 dongle on 3internet (uk) - no access to google services (gmail etc.)"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by Linicks on 2010-12-27
I recently set up two of these 3internet mf112 dongles on Ubuntu, and all works well, pretty much out the box (you have to 'eject' the virtual cdrom drive, as documented elsewhere).

Anyway, the issue I had was that any google services page just times out (connection gets 'interrupted);  this includes signing in, gmail calendar et al.  This is using Firefox and Chrome browsers.  If I used an internet proxy service, these pages do then load, but functionality is affected.

I called the 3internet helpdesk, and of course, not being on microsoft, the guy was lost when going through the usual help scripts :)

This morning I installed Epiphany browser, and hey presto, all google services load in a flash and function properly!

So if you have this issue with 3internet (UK) then use Epiphany for the problem sites/pages.

Nick

---

### Post by Linicks on 2010-12-28
Actually, I just found a way to get firefox to connect to google services using 3internet.

In the dongle settings in network manager, change the APN from '3internet' (this is set when using the wizard at set-up of the dongle automatically) to 'three.co.uk' - now all works great :)

Nick

---

### Post by dESAI on 2010-12-28
> **Linicks said:**
> Actually, I just found a way to get firefox to connect to google services using 3internet.

In the dongle settings in network manager, change the APN from '3internet' (this is set when using the wizard at set-up of the dongle automatically) to 'three.co.uk' - now all works great :)

Nick

HAHA! It works! :D

Nick, I love you... you wonderful human being you!

The Internet is now so damn fast it's freaking me out a bit...

I also do some work online, if you ever need a hand with anything, I'm here for you dude! 

Stay groovy.

---

### Post by Linicks on 2010-12-29
OK, after a couple of hours tonight messing about after work, I finally fixed this properly - it is to do with MTU value.

dESAI, can you please test for me?

Connect with dongle (APN 3internet), and check that access to gmail is 'interrupted'.

Now close firefox (keep internet connection on), open a terminal and issue:

sudo ifconfig ppp0 mtu 1460

Now start firefox again.... and check your mail :)

Nick

---

### Post by Linicks on 2010-12-29
OK, this definitely fixes the firefox 'connection interrupted' issues with googlemail et al (and a lot of other sites, I guess).

After a bit more research, setting a MTU value of 1454 is preferred.

If you wish to make this permanent, edit (as sudo):

/etc/ppp/options

look for #mtu <n> and add just after it:

mtu 1454

and save it.

That's it.  Now connection with dongle, mtu will always be 1454 - and gmail et al works :)

Nick

---

