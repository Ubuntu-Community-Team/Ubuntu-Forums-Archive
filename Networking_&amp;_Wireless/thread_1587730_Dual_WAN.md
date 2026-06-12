---
title: "Dual WAN?"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by EricJD on 2010-10-04
I have a computer set up with 2 NICs and running Ubuntu 10.04. Is there an easy way to set up something like round robin load balancing between the two NICs (two internet connections coming into my apartment)? Both NICs get their IP addresses via DHCP, one is 192.168.1.x and the other is 192.168.55.x.

---

### Post by EricJD on 2010-10-05
Nobody?

---

### Post by sanderj on 2010-10-05
Did you google it? The first hits on [http://www.google.com/search?q=ubuntu+round+robin+dual+nic](http://www.google.com/search?q=ubuntu+round+robin+dual+nic) look like the answers to your question.

---

### Post by Sergius14 on 2010-10-05
Well, I never did this with Ubuntu (even with Linux at all), but I have vast experience with proprietary technologies (Cisco, Fortinet, etc.)

Take VERY care with Round Roubin and dual WANs.

Secure browsing (Home Banking) establishes SSL sessions linked to the IP address. If you change your IP address you can have unexpected logouts from sites that require a login. Even those that are not SSL.

May happens or may not.

Gmail seams to automatically reconnect using cookies, but I know a home banking that inside the SSL, established another SSL link (java applets) linked with the IP. Many other Web Sites don't use cookies and sessions are lost.

It was very frequent receiving calls at the help desk from customers having "unexpected logouts", and always where because Round Robining two or more WAN's.

SonicWALL for ex. have a proprietary protocol specially designed to avoid this (sticking already established sessions).

---

### Post by EricJD on 2010-10-06
> **sanderj said:**
> Did you google it? The first hits on [http://www.google.com/search?q=ubuntu+round+robin+dual+nic](http://www.google.com/search?q=ubuntu+round+robin+dual+nic) look like the answers to your question.

Thanks. I did do some Googling but apparently I didn't use the right search terms. I'll go through the guide on that first link and see where that gets me.

> **Sergius14 said:**
> Well, I never did this with Ubuntu (even with Linux at all), but I have vast experience with proprietary technologies (Cisco, Fortinet, etc.)

Take VERY care with Round Roubin and dual WANs.

Secure browsing (Home Banking) establishes SSL sessions linked to the IP address. If you change your IP address you can have unexpected logouts from sites that require a login. Even those that are not SSL.

May happens or may not.

Gmail seams to automatically reconnect using cookies, but I know a home banking that inside the SSL, established another SSL link (java applets) linked with the IP. Many other Web Sites don't use cookies and sessions are lost.

It was very frequent receiving calls at the help desk from customers having "unexpected logouts", and always where because Round Robining two or more WAN's.

SonicWALL for ex. have a proprietary protocol specially designed to avoid this (sticking already established sessions).

Yes, I understand the concerns about SSL connections and whatnot. Fortunately, this Ubuntu computer won't be used for general web browsing. Its main use will be for downloading files with a multi-threaded download application.

---

