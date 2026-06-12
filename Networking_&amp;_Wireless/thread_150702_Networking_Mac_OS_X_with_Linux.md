---
title: "Networking Mac OS X with Linux"
date: 2006-03-26
forum: Networking &amp; Wireless
---

### Post by shaka on 2006-03-26
I've been trying to figure out how to get my Mac and my Ubuntu box talking using AFP. It was so frustrating that I promised myself that if I figured it out, I would post the solution to save others the same trouble.

I kept getting errorno -5002 (Authentication) problems from my Mac.
Then I started playing around with /etc/netatalk/afpd.conf 
specifically I added  the line-

-uamlist uams_clrtxt.so,uams_dhx.so,uam_gss.so

see  [http://netatalk.sourceforge.net/2.0/htmldocs/afpd.conf.5.html](http://netatalk.sourceforge.net/2.0/htmldocs/afpd.conf.5.html)

And I think the 'uam_gss.so' (Kerberos V Authentication) is what I needed!
I have more tweaking to do, like specify shares etc.. but at least now, I'm not getting the ANNOYING message from my Mac that said "could not connect to server because the name or password is not correct"
More to come...

---

