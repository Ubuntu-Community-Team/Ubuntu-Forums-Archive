---
title: "Samba configuration file"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by Wilco0 on 2009-03-23
Hi. I'm having trouble manually configuring Samba. I've set up a load of shares using the right-click folder options dialog. However when I look in /etc/samba/smb.conf these don't appear, and changes I make to this file (like adding a share) don't take effect when samba is restarted ("/etc/init.d/samba restart"). Is samba using a different configuration file? Otherwise I can't work out what is wrong.

Thanks for any help. Wilco

---

### Post by capscrew on 2009-03-23
When you use the "*right-click folder options dialog*", you are using the Gnome libs to interact with Samba.  The shares are located at /var/lib/samba. The /etc/samba /smb.conf file does not use these shares.  You probably should use one or the other.

---

### Post by Wilco0 on 2009-03-23
Thanks! :)

---

