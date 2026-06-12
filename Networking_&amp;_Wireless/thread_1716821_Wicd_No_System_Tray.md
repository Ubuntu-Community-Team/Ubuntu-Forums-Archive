---
title: "Wicd: No System Tray"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by Nicolexi on 2011-03-29
Hi Everyone,

I just recently updated from Karmic to Lucid Ubunto.  It's been a bumpy adjustment, one thing that I have yet to figure out is why Wicd (My Network Manager) keeps insisting it doesn't have a network tray.  Sometimes, when I switch wireless locations I am told that I have the wrong password and cannot log-on.  Even though I do have the correct password, could these two problems be connected?

Thanks,

Nicole (Newbie)

---

### Post by claracc on 2011-03-29
When I upgraded to lucid from karmic I had a similar problem.

I solved doing:

sudo gedit /etc/init/networking.conf
at the end of this file, i added : exec wicd
save and exit
Then I had to run the daemon in xterm: wicd-client

Then I had to put wicd in the apps in the begining in system --> preferences

---

