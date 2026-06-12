---
title: "putty to .com domain"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by the1udontc on 2009-01-14
Hey folks, I'm new to ubuntu and very rusty with Linux but I'll try to explain this as best I can and hopefully you can help me.

I have two desktop computers setup. One XP one Ubuntu 8.1, I have managed to connect the ubuntu box through an ICS through the windows desktop. What I want to do is be able to putty to my linux box with a .com name instead of the full numerical I.P.. For example SSH to the1udontc.milwaukee.com. If anyone can help me out I'd greatly appreciate it! Thanks.

---

### Post by andrewc6l on 2009-01-14
In Windows, edit c:\windows\system32\drivers\etc\hosts and add your machine name / IP address to it:

192.168.33.21 the1udontc the1udontc.milwaukee.com

Then you'll be able to putty to either the1udontc or the1udontc.milwaukee.com. If your Linux box has dynamic DNS you can still do this, but you might have to edit it now and then as the machine's IP address changes.

(Obviously, 192.168.33.21 is an example IP address - substitute your own :-) )

---

### Post by the1udontc on 2009-01-14
> **andrewc6l said:**
> In Windows, edit c:\windows\system32\drivers\etc\hosts and add your machine name / IP address to it:

192.168.33.21 the1udontc the1udontc.milwaukee.com

Then you'll be able to putty to either the1udontc or the1udontc.milwaukee.com. If your Linux box has dynamic DNS you can still do this, but you might have to edit it now and then as the machine's IP address changes.

(Obviously, 192.168.33.21 is an example IP address - substitute your own :-) )

Thank you!!!! You're a genius!

---

