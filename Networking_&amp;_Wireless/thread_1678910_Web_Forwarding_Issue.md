---
title: "Web Forwarding Issue"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by ryannathans on 2011-01-31
Hey again

not sure if this is ubuntu related.

Web hosting (apache2) on ubuntu server 10.04
I have a dynamic ip so I must use a DDNS if I want to host anything.

I have a domain and DNS hosting through crazydomains.com.au

I set up Web Forwarding from my domain ([www.modifiedgamers.org](www.modifiedgamers.org)) to my DDNS (hitech.selfip.org)

When I go to [www.modifiedgamers.org](www.modifiedgamers.org) it redirects to hitech.selfip.org so I set up cloaking.

When I go to [www.modifiedgamers.org](www.modifiedgamers.org) the url up top my of browser stays static and doesn't add the current page on the eg, EG: [www.modifiedgamers.org/sample](www.modifiedgamers.org/sample)

I am using joomla as a CMS.

Also when I go to [www.modifiedgamers.org/forum](www.modifiedgamers.org/forum) it comes up with a 404 error. However this page exists at hitech.selfip.org/forum.  

How can I get [www.modifiedgamers.org](www.modifiedgamers.org) to work with my server at hitech.selfip.org and still carry everything after the / 

DDNS is hosted free by dyndns.org

---

### Post by ryannathans on 2011-01-31
scratch that, it should 'fix' if I set up a virtual host properly.

Can anyone guide me through creating a virtual host with webmin and apache2

thanks

---

