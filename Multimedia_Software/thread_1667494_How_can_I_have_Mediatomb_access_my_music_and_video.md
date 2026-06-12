---
title: "How can I have Mediatomb access my music and video folders?"
date: 2011-01-14
forum: Multimedia Software
---

### Post by alohanate on 2011-01-14
How can I have mediatomb access my music and video folders?  When I attempt to access "Music" for example, going through /home, I receive this error:

**"Error: could not list directory /home/samwise : Permission denied"**

Is there a way to give permission to mediatomb to access them?  Or is there a way to access them another route because they are shared?

---

### Post by VastOne on 2011-01-15
> **alohanate said:**
> How can I have mediatomb access my music and video folders?  When I attempt to access "Music" for example, going through /home, I receive this error:

**"Error: could not list directory /home/samwise : Permission denied"**

Is there a way to give permission to mediatomb to access them?  Or is there a way to access them another route because they are shared?

Check out the 2nd FAQ here

[_[COLOR="Blue"]Mediatomb FAQ[/COLOR]_]("http://mediatomb.cc/dokuwiki/faq:faq")

---

### Post by alohanate on 2011-01-15
Vastone, if I execute this line,

"[B]# ls -lah // my favorite ls options"

[/B] I think I'm looking for "home" then right?  which the access reads:

d rwxr-xr-x

If I'm the only user, shouldn't that give me permission?  And shouldn't anyone at least have permission to access it?

---

### Post by FokkerCharlie on 2012-01-02
alohanate

Did you make any progress on this?  I'm looking at the same issue at the moment.

It looks to me like MediaTomb runs as root automatically at start, so that's what's causing the permissions issue with your (and my) home folder.

If we can't figure out the permissions, it's possible to stop the service, then start it running with you as the user.  This might be preferable, tbh.

Let me know if you found a better solution.

Charlie

---

