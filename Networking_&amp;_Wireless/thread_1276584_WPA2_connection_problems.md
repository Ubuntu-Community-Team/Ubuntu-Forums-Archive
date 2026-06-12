---
title: "WPA2 connection problems"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by the_real_fourthdimension on 2009-09-27
Hey All

I'm having trouble with all the laptops running 9.04 that I need to connect to multiple networks using WPA2 encryption.  They cannot connect, and ask me to browse for a security certificate.  Is there a place I can download this certificate, or a way I can generate one? 
Thanks.

---

### Post by fluxbuntu on 2009-09-27
make sure you have the package wpasupplicant installed. I had the same problem with my debian laptop until I installed this. I also started using wicd as the connection manager.

---

### Post by kevdog on 2009-09-27
are you using wpa2PSK or wpa2 Enterprise.  The psk version only needs a password, for the enterprise version you need to worry about authentication credentials.

---

### Post by the_real_fourthdimension on 2009-10-07
I installed wpasupplicant, but I am still asked to browse for a security certificate.  Does wicd eliminate this?

---

### Post by the_real_fourthdimension on 2009-10-26
...bump

---

