---
title: "Samba: permissions per user?"
date: 2005-12-12
forum: Networking &amp; Wireless
---

### Post by siorai on 2005-12-12
I've looked through a number of samba guides, but something just isn't getting through to me: how to set up permissions per user. Here's my setup:

My computer is running Ubuntu. I have a VFAT partition an ext3 partition shared. The VFAT is main for sharing files from my roommate's XP box to myself. The ext3 partition is my main storage partition that my roommate also pulls files from. I also run XP on my Ubuntu box through VMWare. 

So what I want to do is to make sure that my roommate has read/write permissions on the VFAT share and read only permissions on the ext3 share. My VMWare XP user can have read/write on both shares. I'm wanting it setup like this, now correct me if I'm wrong here, but because my roommate's XP box shouldn't ever actually write to the ext3 partition right? If that's the case, I just want to make sure that he doesn't accidentally try to write something to it and screw things up.

Currently both users have read/write access to both shares and everything seems to work fine. I have told my roommate not to write to the ext3 share though.

---

### Post by amohanty on 2005-12-12
Take a look at the docs for this:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html)

HTH

---

