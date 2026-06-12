---
title: "iptables - restrictions only to apply to &quot;other&quot; machines"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by qprfact on 2009-12-29
What I am looking to do is, on my network, allow my own machine to have no restrictions in place, but all other rules restricting ports, etc, to apply to other machines.

I've seen examples of how to restrict by Mac address, but essentially I want to do the opposite - something like:

"If Mac address = xyz, allow all

If Mac address not = xyz, apply these rules..."

Is that possible? And if so, how please?

Thanks!

---

### Post by Lord_ on 2009-12-29
IPtables can be difficult to configure, I tend to 'cheat' and administer it from the webmin module. It might be worth looking into this, if you choose to install it you can just do

sudo apt-get install webmin

Once you loaded webmin, do a search for IPtables and it has a good rule creator.

---

### Post by qprfact on 2010-01-24
Solved here - [http://ubuntuforums.org/showthread.php?t=1372002](http://ubuntuforums.org/showthread.php?t=1372002)

---

