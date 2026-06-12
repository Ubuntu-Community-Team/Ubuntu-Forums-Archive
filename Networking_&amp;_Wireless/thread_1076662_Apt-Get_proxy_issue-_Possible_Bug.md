---
title: "Apt-Get proxy issue- Possible Bug"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by dwavidbwyant on 2009-02-21
Ubuntu 8.10
at work, I must connect thru the proxy to use the internet.
this is accomplished by setting the system wide proxy in prefrences.
it works fine, apt-get easily downloads what I need.  When I come home, with a direct connection, I kill the proxy, which works fine for everything 
I need execpt apt-get.  
Apt-get still tires to use the proxy from work, while all other apps recognize that i turned off the proxy.

this is what comes out. (fwd.xxxx.edu is the "disabled" proxy)

Could not resolve 'fwd.xxxx.edu'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main php5-cli 5.2.6-2ubuntu4.1

---

### Post by thefluxster on 2009-06-25
I have the same annoyance and have been unable to find a solution to the problem other than rebooting after changing the global proxy settings.  Very annoying...

---

### Post by thefluxster on 2009-06-25
> **thefluxster said:**
> I have the same annoyance and have been unable to find a solution to the problem other than rebooting after changing the global proxy settings.  Very annoying...

Correction: You can also open Synaptic Package Manager > Settings > Network.  Just click "Apply" and then close it.  Should work after that.  Obviously a workaround, but better than rebooting.

---

