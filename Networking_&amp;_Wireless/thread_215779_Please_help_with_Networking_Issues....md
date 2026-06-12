---
title: "Please help with Networking Issues..."
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by cynon83 on 2006-07-14
I have no idea why this is happening, but I'm having HUGE problems with networking, and one of the reasons is that something in Ubuntu keeps overwriting my resolv.conf file. This networking issues is very difficult for me to figure out as it is, and when the system keeps restoring files that I've changed, it's a completely losing battle.

Does anyone have any idea why this file in particular is being overwritten? Once ubuntu 'corrects' it, my network is hosed and I'm back to step one.

And about the networking:
When I go to a web page, even though I can ping the page, often, firefox will say done, but the page will be blank. If I get, say, google to come up, then type in a search, I get a blank page, but then the address bar reads: [http://www.google.com/?f](http://www.google.com/?f)

This will happen if I click on links sometimes as well, with any web page. Sometimes the page comes up, sometimes it's just a blank page, and sometimes I get the /?f at the end of the url.

None of the windoze boxes on my network do this, but the really nasty thing is that my server, which has been up and running over a year (P3-450, mandrake 10) has started doing this as well. And it's worked fine for over a year.

This leads me to believe that it could be the router, but if it was, then the windoze boxes should be doing this too, and they're not. Plus, I haven't changed anything in the router for a long, long time.

Oh yeah, and even though it takes a long time, when I can't get a web page to come up, I can still ping the page.

Any ideas?

---

### Post by mips on 2006-07-14
There is a fix for this but I'm to tired to look for it right now & going to bed.

Try searching for 'resolv.conf' or 'dhcp' , it's there you just have to find it.

---

### Post by bigken on 2006-07-15
take a look at reply 3 here this could the same problem as I had 
[http://www.ubuntuforums.org/showthread.php?t=215461](http://www.ubuntuforums.org/showthread.php?t=215461) ;)

---

### Post by cynon83 on 2006-07-17
Well, apparetnly, my resolv.conf keeps being overwritten by the system.  Once I edit it, everything works until I reboot.  Any ideas on why ubuntu feels the need to overwrite my config files?

---

### Post by mips on 2006-07-17
Look at here:
[http://www.ubuntuforums.org/showthread.php?t=128254](http://www.ubuntuforums.org/showthread.php?t=128254)

---

