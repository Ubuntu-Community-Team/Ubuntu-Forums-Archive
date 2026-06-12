---
title: "Can't connect to sites served from Amazon's EC2 cloud"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by miromiro on 2011-04-08
Over the last 3 or 4 days, I have been unable to load sites that serve their images, scripts and whathaveyou from Amazon's cloudfront domain.

Sites include:
[http://bitbucket.org/](http://bitbucket.org/)
[http://blekko.com/](http://blekko.com/)
[http://quora.com/](http://quora.com/)

I have made no changes to any of my networking files, hosts{allow,deny}, or dns settings.

Connections don't provide any errors, just continually fail to load. Stopping the page load after a while reveals the raw HTML in some cases (quora and blekko).

Tested in Firefox, Chromium, Midori and Vimprobable.

I have booted into another distro and pages resolve immediately.

I have disabled IPV6 and my firewall - to no effect.

Any pointers would be welcome.

---

### Post by cjhabs on 2011-04-08
Are you using local dns caching - maybe with dnsmasq - and the location has changed?

---

### Post by miromiro on 2011-04-08
Thanks cjhabs: good idea. I flushed the cache and still no joy...

Edit: I should mention that I can retrieve the pages without issue using w3m or Lynx.

---

### Post by miromiro on 2011-04-09
I've been back through /var/log/dpkg.log and there is nothing there that is obvious.

Booted from an Ubuntu Live CD - where it works as expected - and copied over all of the network settings and /etc/{hosts,resolv} files. No dice.

Loading a page, like bitbucket, sees the status bar move quite quickly when sourcing files from bitbucket.org but then just freezes when it tries to access the EC2 server, $string.cloudfront.net

The browser remains blank and, even if left for 45+ mins, returns no errors...

Other machines on the network can load the pages without issue and, as I said above, I can ping these sites and access them without problems via a text browser like w3m.

Can anyone point me at some other areas I should be investigating?

---

### Post by miromiro on 2011-04-09
Fixed by uninstalling Firestarter and writing new rules using ufw.

---

