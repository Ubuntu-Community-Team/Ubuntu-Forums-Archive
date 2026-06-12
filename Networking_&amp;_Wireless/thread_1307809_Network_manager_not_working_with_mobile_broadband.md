---
title: "Network manager not working with mobile broadband"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by Jackyboy86 on 2009-10-31
I've been using a ZTE MF627 '3' dongle under 9.04 - and got it working with moblin beta using the guide/software at [www.greenhughes.com]("http://www.greenhughes.com"). All good.
Now, under 9.10 - i'm being forced to use wvdial as network manager is claiming to have connected, but it's not actually allowing me to access the web.
This wouldn't be a problem, I quite enjoy using wvdial (as it's a load faster connecting than netman), but apparantly ubuntuone requires a netman connection in order to 'add a computer'.

I've become very fond of ubuntuone (although through gritted teeth over the whole 'closed source' fiasco), and so I need to get Network Manager working.
Any ideas what log I need to be looking at/quoting here?
Anyone else encountering the same problem?

EDIT: Now solved.

---

### Post by Jackyboy86 on 2009-11-01
Bump! Can anyone help?
I don't want to have to keep 9.04 if it's sole use is going to be uploading to a cloud!

---

### Post by pdc on 2009-11-01
so you have solved this?

Tell the forum what has worked (to help others)

---

### Post by Jackyboy86 on 2009-11-02
Yes, I solved it.
Karmic appears to be incorrectly setting up 3 PAYG devices
It leaves the name & password field blank (instead of filling them with 'anything')
And the APN, as in Jaunty is wrong.
It should be 3services, not 3internet.

I think that covers it!

---

