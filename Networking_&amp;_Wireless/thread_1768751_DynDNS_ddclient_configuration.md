---
title: "DynDNS ddclient configuration"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2011-05-27
Where are there good instructions to configure the  [DynDNS update client](https://www.dyndns.com/support/clients/unix.html)?  It is not updating my IP number.

---

### Post by Lars Noodén on 2011-05-27
It turns out there were mistakes in the config file. All set now.  Installing via the repository activated the installation wizard which asked the right questions.

---

### Post by iclestu on 2011-05-27
a wizard?!

I never found no wizard! Mine was quite basic and I was able to follow the template for the config file in the knowledge base at dyndns but id have liked a wizard! :)

---

### Post by Lars Noodén on 2011-05-27
It's there in Natty.  Try **dpkg-reconfigure ddclient** to see the wizard.  I needed to run it twice to get the right values typed in correctly.

---

### Post by iclestu on 2011-05-27
I installed from Natty.... Hmmmm No matter, its working and thats the main thing...

---

### Post by Starpoint on 2011-05-29
I just installed ddclient and the wizard ran, put in my info for my FTP server (dns323) but I am behind a Uverse 2wire router. I have the router forwarding port 21 over to the static IP of the FTS server 

has anyone had any luck with this set up?

---

