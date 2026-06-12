---
title: "Jaunty hangs a minute or so during boot when MTA sendmail is installed"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by planetLars on 2009-06-15
Hello,

Jaunty hangs a minute or so during boot when MTA sendmail is installed.

Does anyone have any knowledge on how to get that time to the usual milliseconds of other services? If so, tell! :-)

Best

Lars

---

### Post by planetLars on 2009-06-16
anyone?

---

### Post by mpokrywka on 2009-06-17
I suspect this is a "problem" with DNS. I guess sendmail tries to resolve some hostnames on startup (i.e. your machine's name), but during startup no network connection is present - I am guessing, you are using Network Manager.
I don't know how to solve it for sendmail IF that is your problem.
On my laptop I have exim installed and exim has this debconf option "Keep number of DNS-queries minimal (Dial-on-Demand)?" set to YES  (sudo dpkg-reconfigure exim4-config)

---

### Post by planetLars on 2009-06-17
Hi, thanks. My laptop is indeed not connected during boot (wireless connects later). I haven't found an option to reduce the timeout yet.

Lars

---

