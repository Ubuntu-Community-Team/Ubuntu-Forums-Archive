---
title: "XMLTV error &quot;Bad hostname&quot;"
date: 2008-09-17
forum: Multimedia Software
---

### Post by NickD-NLUG on 2008-09-17
I keep receiving the error:

usernamehostname$ ./tv_grab_uk_rt 

+--------------------------------------------------------------------------+
| All data is the copyright of the Radio Times website and the use of this |
| data is restricted to personal use only. <http://www.radiotimes.com>     |
+--------------------------------------------------------------------------+

XMLTV::Supplement: Failed to fetch [http://supplement.xmltv.org/tv_grab_uk_rt/channel_ids:](http://supplement.xmltv.org/tv_grab_uk_rt/channel_ids:) 500 Can't connect to supplement.xmltv.org:80 (Bad hostname 'supplement.xmltv.org').

I can resolve the hostname using any other program, I can access the URL xmltv is trying to get to using browsers, so my XMLTV or Perl installation appears to be borked in some way.  Any suggestions on what I should look at first to try and resolve this?

As strace shows a whole load of errors I'm happy to post the edited highlights if that will help...

---

### Post by NickD-NLUG on 2008-09-18
Found the problem... an extremely long entry in my /etc/hosts file, after 127.0.0.1, as an ad-blocking feature using the MVPS lists, was causing this issue.

A bit rubbish... but glad I've got it fixed :)

---

