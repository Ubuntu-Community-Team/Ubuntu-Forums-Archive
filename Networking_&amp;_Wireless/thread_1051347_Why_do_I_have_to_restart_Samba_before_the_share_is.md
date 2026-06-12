---
title: "Why do I have to restart Samba before the share is available to other machines?"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by icheyne on 2009-01-26
Why do I have to restart Samba before my XBMC or my other desktop recognise the share?

It worked when I set it up, but now I have to restart every time.

sudo /etc/init.d/samba restart

testparm works fine.

---

### Post by unemployed96 on 2009-02-20
i've got the same issue.  PM me if you figure it out and i will do the same

---

### Post by icheyne on 2009-05-01
This is fixed in Ubuntu 9.04.

---

### Post by Vock on 2009-10-14
I'm using 9.04 and still have this issue.

---

### Post by qqi239 on 2009-10-20
I am running pretty recent 9.04 with statically configured ip (I am using wicd, though) and the issue is still there - are there any news or hope on resolving it?

---

### Post by Vock on 2009-11-27
I'm under the impression that samba starts up before your network manager resolves your IP, so your start-up IP is always for localhost, and not what you want it to be. I'd think it would be something different considering you're on a static IP, but i'm not really sure.

---

