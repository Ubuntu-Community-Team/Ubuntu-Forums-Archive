---
title: "Monitor Traffic?"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by DeMartini on 2010-08-26
I set up a ssh file server allowing a handful of people guest accounts that can access media files. I was wondering if I can monitor the traffic, time in/out, uploads etc??? Thanks

---

### Post by Lars Noodén on 2010-08-27
You could consider having the connection going via [xinetd](http://manpages.ubuntu.com/manpages/lucid/en/man5/xinetd.conf.5.html).  One configuration directive there is **log_on_success** which has provisions to log the duration of the session.   Uploads are another matter.  sftp-server does some logging now, but increased levels of logging can violate privacy rather severely and should be used only for debugging and only for as short a period as possible.    

Otherwise you could use iptables and track the SYN with FIN/ACK associated with opening and closing the sessions.  That would not be as easy as xinetd. 

If more than one SSH session is sent over the single TCP/IP session, using multiplexing, then those stats won't be accurate.

---

### Post by SlugSlug on 2010-08-27
> **DeMartini said:**
> I set up a ssh file server allowing a handful of people guest accounts that can access media files. I was wondering if I can monitor the traffic, time in/out, uploads etc??? Thanks


logging etc may not be nice but if you just wanted to have a quick look at whats going on then
iftop
iptraf
tshark
are useful, and to check what files are in use
sudo lsof |grep [username used to connect to you]

---

