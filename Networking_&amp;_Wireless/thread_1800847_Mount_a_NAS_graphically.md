---
title: "Mount a NAS graphically"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by Benjaperson on 2011-07-09
Can I mount a WD My Book World Edition NAS in Ubuntu 11 without extensive terminal work?   The NAS has a static ip, it can be ping'd from Ubuntu, and my Windows machines access it just fine, no passwords required.

I have not been able to find a way to make this work.  Nothing against the terminal per se, it's just still a little too unfamiliar and I keep hitting error road blocks on this one.

Can it be done simply with Gnome?  With Nautilus?  How?

---

### Post by Morbius1 on 2011-07-09
What happens if you go to: Nautilus > Network > Windows Network 

Can you not see the NAS?

---

### Post by Benjaperson on 2011-07-09
Nothing.  Not even if I check 'show hidden files'.

---

### Post by Morbius1 on 2011-07-09
Open up a terminal and type:

```
nautilus smb://ip-address-of-the-NAS-device
```

If you connect bookmark it.

If you can't, post the error messages it gives you.

---

### Post by Benjaperson on 2011-07-09
Wow! That's it!  Thanks.

SOLVED.

---

