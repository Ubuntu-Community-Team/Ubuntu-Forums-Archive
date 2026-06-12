---
title: "Can only access google site."
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by chad.stout on 2009-08-26
I have a very strange issue.  Recently made the switch from Windows to Ubuntu on my main box (no issues at all here), and figured I should do the same I use for a media box I use.

So everything is installed just fine, however on the media box I can't access any site other than a google site (e.g., google.com, gmail.com, etc.)  Every other site I've tried simply sits at "waiting for www.domain.com...".  I was thinking it had to do with ipv6 being defaulted on, however I disabled it (even down-graded from 9.04 to 8.04).

I can ping other sites and access everything just peachy from my other main machine, so I know it's not likely to be something with my network/router.

I'd really prefer not going back to windows, but I can't even access any repositories to download updates and drivers!  Any help would be much much appreciated!

---

### Post by Charly85551 on 2009-08-28
Hi, from what you are reporting it looks like everything on the side of the router is working with your main box so something is not right on your media box. Could it be that something is not set properly with your name server? From your description it looks like your router is acting as name/DNS server which is pretty much the standard today. 
Have a look at your */etc/resolv.conf* file. Go into terminal mode and enter *sudo gedit **/etc/resolv.conf *and make sure that you have a line like *nameserver 192.168.1.1* (just replace 192.168.1.1 with the IP-address of your router!).
After that every Internet URL should be interpreted and translated by your router and thus giving the response you are expecting on your media machine.:)
cheers

---

