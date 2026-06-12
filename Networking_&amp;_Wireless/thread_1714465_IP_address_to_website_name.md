---
title: "IP address to website name"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by woodzykiler on 2011-03-25
how do i teun an IPaddress in to a website name that i payed for? useing apachie 2. think stupid when you are giging me an answer please as in what line number to enter what code(s) i use notepad++ to edit system files with coreftp and putty by my side.

---

### Post by .:PiXi²:. on 2011-03-25
Contact your DNS provider (where you bought the address) and ask them to update your record with your IP address. Probably you've received login details to a control panel where you can setup these things for yourself.

---

### Post by woodzykiler on 2011-03-25
> **.:PiXi²:. said:**
> Contact your DNS provider (where you bought the address) and ask them to update your record with your IP address. Probably you've received login details to a control panel where you can setup these things for yourself.
 
sorry maby i should of told you i have a VPS thro the same people as my DNS i payed for i did link the DNS with my VPS nameserver and IP, but suppert said i have to do something on the VPS in apanchie2 for it to work right..

---

### Post by woodzykiler on 2011-03-25
can i please get some help i have had meny views so far. maby a mod can put this in the right place?

---

### Post by woodzykiler on 2011-03-27
> **woodzykiler said:**
> can i please get some help i have had meny views so far. maby a mod can put this in the right place?
 s

---

### Post by CharlesA on 2011-03-27
If the VPS has it's own IP, then all you would have to do would be update the host record (A record) of your domain name to point to the ip of the VPS.

---

### Post by dacoolio on 2011-03-27
You'll need to go to your registrar and set it up that way. I don't know where you bough your, but I got mine from GoDaddy and there's a domain control panel type thing where you can update all the records for the domain. Hope that helped

---

