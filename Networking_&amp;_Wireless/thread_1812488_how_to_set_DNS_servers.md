---
title: "how to set DNS servers?"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by ubto66 on 2011-07-26
Ubuntu 10.04lts

a) right click wlan icon.
b) edit connections.
c) wireless.
d) wlan.
e) edit.
f) ipv4settings.
g) manual.
h) dns servers.

Isn't this the place to change the dns servers?
If I input dns server fx googles 8.8.8.8,8.8.4.4
then it's like the system asks for search domains.
Must I input something there, or how do I set the dns servers?
Thank you.

---

### Post by SlugSlug on 2011-07-26
I normally edit 
/etc/resolv.conf

add 

namesevrer 8.8.8.8


or /etc/networking/interface

---

### Post by adil_mhaisker on 2011-07-26
The thing you did is ENOUGH for DNS queries.
What you are asking is for Search Domain. This is only required if you are in big organization with some Domain Name. For e.g. your domain name is xyz.com. Then you can put this "domain name" in Search Domain box so that whenever you will say put command: **ping www** , it will automatically **ping [www.xyz.com](www.xyz.com)**.

Hope this answers your question.;)

If you are at home, you can leave it empty.

---

### Post by haqking on 2011-07-26
> **ubto66 said:**
> Ubuntu 10.04lts

a) right click wlan icon.
b) edit connections.
c) wireless.
d) wlan.
e) edit.
f) ipv4settings.
g) manual.
h) dns servers.

Isn't this the place to change the dns servers?
If I input dns server fx googles 8.8.8.8,8.8.4.4
then it's like the system asks for search domains.
Must I input something there, or how do I set the dns servers?
Thank you.

or configure DNS servers on your router and leave it at that.

nambench helps you find your fastest one, though there are other methods.

i personally use it [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

---

### Post by ubto66 on 2011-07-26
What you are asking is for Search Domain. This is only required if you are in big organization 
If you are at home, you can leave it empty.

Case is, that ubuntu won't let me close the window if I don't type something in the
'search domain' box.

---

### Post by ratcheer on 2011-07-26
> **SlugSlug said:**
> I normally edit 
/etc/resolv.conf

add 

namesevrer 8.8.8.8


or /etc/networking/interface

Ubuntu overwrites this file back to the default every few minutes unless some goofball package is installed to prevent it. So stupid.

The package is called resolvconf.

Tim

---

