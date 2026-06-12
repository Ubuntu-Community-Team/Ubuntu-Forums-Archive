---
title: "mythtv-htacess is missing"
date: 2013-06-07
forum: Mythbuntu
---

### Post by odror on 2013-06-07
I have the latest version of mythtv/mythweb (ppa 0.26 fixes)

.htacess is a symbolic link to /etc/mythtv/mythweb-htaccess, but the second file is missing

Is this a bug or I have a problem in my system.

my OS is ubuntu 13.04 x86_64

Thanks

---

### Post by MagnusL on 2013-06-08
Hi!

I just upgraded my backend to ubuntu 13.04, and I see the same here - no .htaccess, the symbolic link is there by no target for it. And my mythweb is blank - shows nothing. Same with you?

My problem was solved by upgrading to mythtv 0.26, following [http://code.mythtv.org/trac/ticket/10504](http://code.mythtv.org/trac/ticket/10504)

Best, 

Magnus

---

### Post by odror on 2013-06-08
> **MagnusL said:**
> Hi!

I just upgraded my backend to ubuntu 13.04, and I see the same here - no .htaccess, the symbolic link is there by no target for it. And my mythweb is blank - shows nothing. Same with you?

My problem was solved by upgrading to mythtv 0.26, following [http://code.mythtv.org/trac/ticket/10504](http://code.mythtv.org/trac/ticket/10504)

Best, 

Magnus

My mythtv was already on 0.26 fixes. The following fixed my problem. [http://francisfisher.me.uk/problem/2012/secure-mythweb-with-mythbuntu-12-04/](http://francisfisher.me.uk/problem/2012/secure-mythweb-with-mythbuntu-12-04/)

---

