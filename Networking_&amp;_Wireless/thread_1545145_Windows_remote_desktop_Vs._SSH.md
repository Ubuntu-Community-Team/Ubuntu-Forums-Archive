---
title: "Windows remote desktop Vs. SSH?"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2010-08-03
What are the pros and cons of windows remote desktop compared to X-windows over SSH on linux?

---

### Post by pricetech on 2010-08-03
In my opinion there's no comparison.

SSH is inherently more secure and gives you the option of doing away with password authentication altogether eliminating the concern about weak passwords.

You can also change the port you use for SSH quite easily.  It takes a registry hack under windows to change the RDP port and I'm not even certain it will work if it's changed. (I haven't tried it yet)

You can also use the same security for file copy, making it much better than windows file sharing.

There are SSH clients that work under windows and I use them on windows boxen I support with no problems at all.

---

