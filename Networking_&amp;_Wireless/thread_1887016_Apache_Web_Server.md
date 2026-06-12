---
title: "Apache Web Server"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by createdcreature on 2011-11-26
My router has a settings page that is accessed by typing in '192.168.0.1'. Will this affect a web site hosted LOCALLY, using Apache with Ubuntu 11.10 32-Bit Server with Apache, MySQL, and PHP (LAMP, but MySQL and PHP I do not intend to use).

---

### Post by lisati on 2011-11-26
Short answer: probably not.

Your web server will probably have a separate (different) IP address on your local network.

---

### Post by createdcreature on 2011-11-26
Will 'localhost' work?

---

### Post by Chumber on 2011-11-26
> **Robert Moyse said:**
> Will 'localhost' work?

Yes, opening [http://localhost](http://localhost) in your browser will access your website (obviously, the machine you type this on must be the machine with the Apache server on)

---

### Post by createdcreature on 2011-11-30
Will you be able to access the site just by typing in to your browser (from another computer, away from the network), my global IP, e.g. **.*.***.***.

---

