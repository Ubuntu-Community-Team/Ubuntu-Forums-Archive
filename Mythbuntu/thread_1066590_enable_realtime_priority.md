---
title: "enable realtime priority"
date: 2009-02-11
forum: Mythbuntu
---

### Post by iitywygms on 2009-02-11
From this link

[http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4](http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4)

I edited
/etc/security/limits.conf and put this in.

* - rtprio 0
* - nice 0
@audio - rtprio 50
@audio - nice 0

But I still get this when running mythfrontend.
Realtime priority would require SUID as root.

I have rebooted

Im running mythbuntu 8.04.01

Any ideas?

thanks

---

### Post by jboehm on 2009-02-11
I tried to get realtime piority running with Mythbuntu 8.10 but didn't have any luck.  Hope you find the answer and share it here when you do. -- Jon

---

### Post by ian dobson on 2009-02-11
Hi,

just use chmod +s to set the sudo bit for mythfrontend.real .

Regards
Ian Dobson

---

### Post by iitywygms on 2009-02-11
> **ian dobson said:**
> Hi,

just use chmod +s to set the sudo bit for mythfrontend.real .

Regards
Ian Dobson

I think I tried that and it did not work.  (chmod a+s /usr/local/bin/mythfrontend /usr/local/bin/mythtv) and according to the above mentioned thread, this is not a very good way.  It is a security risk.

So now another question.  How do I change it back to what it was.

---

### Post by iitywygms on 2009-02-11
Fixed!

edit /etc/security/limits.conf 

add this

* - rtprio 0
* - nice 0
@mythtv - rtprio 50
@mythtv - nice 0

---

