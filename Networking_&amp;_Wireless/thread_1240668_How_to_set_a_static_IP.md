---
title: "How to set a static IP"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by The Pinny Parlour on 2009-08-14
Hello

I am trying to set a static IP in my Ubuntu computer.  Usual methods don't seem to work, (right click 'edit connections').

I always have to set it back to DHCP and it works.  

Thanks

---

### Post by SoftwareExplorer on 2009-08-15
Did you set DNS addresses when you tried it? That was what I was doing wrong. IIRC 4.2.2.1, 4.2.2.2, 4.2.2.3, 4.2.2.4, 4.2.2.5, 4.2.2.6 are ones that I used and worked. (You really only need one or two, but I'm just a little perfectionist)

Second, your router could support assigning addresses by MAC address, which would have the same result as a static address, but might work around your problem.

---

### Post by The Pinny Parlour on 2009-08-15
> **SoftwareExplorer said:**
> Did you set DNS addresses when you tried it? That was what I was doing wrong. IIRC 4.2.2.1, 4.2.2.2, 4.2.2.3, 4.2.2.4, 4.2.2.5, 4.2.2.6 are ones that I used and worked. (You really only need one or two, but I'm just a little perfectionist)

Second, your router could support assigning addresses by MAC address, which would have the same result as a static address, but might work around your problem.

Yes I did set a DNS.  Hmmmm.  You think I'd be used to Ubuntu's weirdness by now but little things that should work still seem to bite me.

---

### Post by Iowan on 2009-08-15
Does it fail to *get* the static address, or does it just fail to work *with* the static address?

---

### Post by jongkind on 2009-08-15
I have very good experiences with wicd instead of network manager. It can be downloaded from here:

[http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

---

### Post by superprash2003 on 2009-08-15
post output of **ifconfig** and try pinging your router via ip

---

### Post by SoftwareExplorer on 2009-08-15
Also, there's still the possibility of setting the router to assign the same address to your computer every time. Your computer would still think it is getting a dynamic address, but the router would be giving it the same one every time.

---

