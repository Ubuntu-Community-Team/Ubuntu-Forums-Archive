---
title: "samba service will not start automatically"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by ffoeg on 2009-01-31
I just did a fresh install of Ubuntu 8.1 desktop. 

I'd like to use it as a samba server. I had no trouble getting that setup. But if I reboot it, the samba has to be started manually.
How can I get this service to startup automatically, prior to logging in? 

I've already checked system->aministration->services and system->prefernces->sessions; samba is set to startup (despite this, it doesn't). But these settings seem to be settings for that specific Ubuntu profile, services that kick in after logging in as that user. 
I would like the samba service to startup whether someone logs in on that workstation or not. Is that possible (this is how samba behaved in prior versions of Ubuntu, as well as Suse)? If so, how?
Thank you.

---

### Post by Prospero2006 on 2009-01-31
you could add a line to /etc/rc.local if you are having problems, but somehow that doesn't sound right. I run samba on intrepid without any hitches. 

/etc/rc.local
```

/etc/init.d/samba restart

```

---

### Post by ffoeg on 2009-02-01
Thank you Josh. When I entered "sudo" in front of the restart command in that script, it worked. I appreciate your help.
Thanks

---

