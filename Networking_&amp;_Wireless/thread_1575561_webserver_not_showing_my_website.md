---
title: "webserver not showing my website"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by Lakeside5 on 2010-09-15
Just wondering if someone can 'talk me through this' a little, and see where I went wrong. I've actually gotten a webserver (hardy heron, server edition) working before and had a Joomla site up I could find on the net. But I did a fresh install of Lucid Lynx (desktop edition, that I added some packages to to use as a server). Between the router (wrong ip address?), port forwarding (set right?), my domain nameservers (godaddy) and the DynDNS service I use (for dynamic ip) I must have a wrong setting because, my joomla website shows up at localhost, but not 'out there' so to speak. I would appreciate any help, would like to get this site out there and working soon, as it's one I'm just doing free for a Community Garden. thanks!

---

### Post by dmizer on 2010-09-16
Have you actually tried to access the site from a machine that is not physically connected to the same LAN as your www server?

---

### Post by SeijiSensei on 2010-09-17
Go to machine outside your network, open a browser, and enter [http://your.servers.ip.address/](http://your.servers.ip.address/) in the address bar rather than a hostname.  Do you see any site at all?  What is it?  If you see something other than your site, you need to delve into the configuration files for your web server.  If, as I suspect, you're using Apache, you'll need to look at httpd.conf and change the "DocumentRoot" directive to point to the directory where your site's index.html file is kept.

If you're hosting multiple sites on the machine, you'll need to explore how to use the "VirtualHost" directives.

---

