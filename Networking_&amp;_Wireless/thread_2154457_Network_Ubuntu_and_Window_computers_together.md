---
title: "Network Ubuntu and Window computers together"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by HarmonicaGuy on 2013-06-14
Is it posible to network ubuntu computer to windows computer?

---

### Post by Iowan on 2013-06-14
Certainly! Getting them to talk is not the tricky part - sharing stuff is...

---

### Post by HarmonicaGuy on 2013-06-15
I'm still learning ubuntu. I have my ubuntu and windows7 computer wired to the dsl router. Is there more I need to know? How do I get them to talk? And how can I share stuff?

---

### Post by 2F4U on 2013-06-15
What exactly want to do? If you want them to share files then look into Samba:

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Else provide more information about what you intend to do.

---

### Post by HarmonicaGuy on 2013-06-15
Thank you! I'll try this. All I really want to do is print from my Ubuntu to my windows.

---

### Post by HarmonicaGuy on 2013-06-17
How do I configure Firestater Firewall

---

### Post by Cheesemill on 2013-06-17
> **HarmonicaGuy said:**
> How do I configure Firestater Firewall

Don't use it. The Firestarter project has been dead for years. If you've already installed it then it's best to uninstall it before using anything else otherwise the 2 applications will conflict with each other.

If you want a GUI for Ubuntu's built in firewall then use [Gufw]("apt://gufw").

---

### Post by HarmonicaGuy on 2013-06-19
Yes, I have learned about firestater a few days ago and have removed it from my system. I have added Gufw. 

Just one question, 
I have udp ports in the "listing reports";
udp 4404 avahi-daemon 
udp 5353 avahi-daemon  
udp 68 dhclient
 udp6 33730 avahi-daemon
 udp6 5353 avahi-daemon.

I added udp 5353/udp as "deny in" to the gufw. Is this why udp 5353 and the udp6 5353 avahi-daemon are both showing in green?

Is this okay?

---

