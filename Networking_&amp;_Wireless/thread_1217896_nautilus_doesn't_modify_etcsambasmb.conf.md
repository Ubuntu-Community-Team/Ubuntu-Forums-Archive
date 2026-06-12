---
title: "nautilus doesn't modify /etc/samba/smb.conf ?"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-07-20
I opened nautilus and shared the folder by right-click > sharing options. The folder was shared successfully. But the content of /etc/samba/smb.conf didn't change. Why is that?

---

### Post by swerdna on 2009-07-20
> **afeasfaerw23231233 said:**
> I opened nautilus and shared the folder by right-click > sharing options. The folder was shared successfully. But the content of /etc/samba/smb.conf didn't change. Why is that?

Because Nautilus does not make classical shares. It makes "usershares". Usershares have their config files in /var/lib/samba/usershares. Check it out.

There's a bit more about that in the section titled: "Setting up a Samba Server (Browsing and Sharing)" in the tutorial here: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by afeasfaerw23231233 on 2009-07-20
thanks

---

