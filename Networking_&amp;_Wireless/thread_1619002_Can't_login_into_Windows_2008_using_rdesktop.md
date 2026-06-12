---
title: "Can't login into Windows 2008 using rdesktop"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by soulreaver1 on 2010-11-11
Hi,

I have problem with login into Windows 2008 server usning rdesktop 1.6. While I'm connect Windows 2008 host, prompts username and password i get an error: "Wrong username or password" but i'm sure that username and pass are correct (I can connect this server using windows Remote Desktop). My OS is Ubuntu 10.04 64-bit.

---

### Post by tecnico on 2010-12-10
Try:  "  rdesktop -d domain  -u user machine  "     I had the same problem trying to login to a Win2008 server in a domain.  I could login to WinXP but not Win2008. After adding the username and domain on the command line I was able to login.  Hope it helps.

---

