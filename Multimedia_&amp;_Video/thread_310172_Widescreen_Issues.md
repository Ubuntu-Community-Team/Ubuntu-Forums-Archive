---
title: "Widescreen Issues"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by catacon on 2006-11-30
Hi all,
I have a ViewSonic VA1912wb 19" widescreen monitor that I have been trying to get working on 6.06.  I have tried following some of the threads about here, but nothing has worked, I always get stuck with 1024x768 or something like that instead of the 1440x900 resolution that I want.  If someone could walk me through what I need to edit in xorg.conf to get this to work, I would be very appreciative.

Specs:
Athlon XP 2600+
Onboard Via video
Ubuntu 6.06

Thanks!

---

### Post by taurus on 2006-11-30
Have you tried running 

```
sudo dpkg-reconfigure xserver-xorg
```
to reconfigure your monitor?

---

### Post by catacon on 2006-11-30
Yes, and it gives me every resolution except 1440x900 even when I select it.

---

### Post by camilluk on 2006-12-01
I had a similar problem with my ATI card. I don't know in your case, but in mine for some reason the correct resolution only applied to user "root". So I ended up creating a new user while being root, 
and the new user acquired the proper resolution.

---

