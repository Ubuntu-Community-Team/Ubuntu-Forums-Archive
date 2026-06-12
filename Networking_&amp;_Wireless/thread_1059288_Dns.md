---
title: "Dns"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by chiefbutz on 2009-02-03
There is an Ubuntu system that I do not have root privileges on, but I have a webpage on it. I was wondering if there was a way to bind my domain name that I use elsewhere to that web space without having to go through the admins and such since that can be troublesome. I don't have malicious intent, I am just curious if it is doable.

---

### Post by chiefbutz on 2009-02-06
Bump.

Is this possible? A yes or no would be great!

---

### Post by TTFN on 2009-02-06
> **chiefbutz said:**
> Is this possible? A yes or no would be great!

Maybe.

It depends on how the Admins have your website set up.  If it's a dedicated website with a dedicated IP then you should be able to creating a DNS A record and point it to that IP.

However, if the Admins are using a shared IP, or your website is a sub directory of the Admin's main website ([www.mainweb.com/mydirectorysite](www.mainweb.com/mydirectorysite)), then you would have to get the Admins involved.

Hope this helps.

---

### Post by chiefbutz on 2009-02-06
Yep, it is a shared IP. Thank you

---

