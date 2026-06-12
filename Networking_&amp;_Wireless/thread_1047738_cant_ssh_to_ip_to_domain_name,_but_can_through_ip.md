---
title: "cant ssh to ip to domain name, but can through ip"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by christoforever on 2009-01-22
So I just set up a domain name [www.christoforever.com](www.christoforever.com) its pretty lame but its just a start. I cant however ssh into christoforever.com like   

ssh [email]cdancy@christoforever.com[/email]

I can however do ssh cdancy@###.##.##.### and that works just fine. I was simply wondering if there was something I had to set to make this work.

---

### Post by ooobooontooo on 2009-01-22
Did you set up the DNS server, so the computer can convert domain name to ip address?

---

### Post by christoforever on 2009-01-22
The only thing I did was forward and mask the domain name at godaddy meaning i said to forward christoforever.com to ##.##.##.##

---

### Post by ooobooontooo on 2009-01-22
My understanding is that you need to set up a DNS server so that once you contact domain, it will send you back the ip address so that ssh can establish connection with the ip address. Without the DNS server, you'll contact the domain but ssh won't know the ip so it won't be able to establish connection....I think.

---

### Post by nishv on 2009-01-22
You need to add an A Record on the DNS to point christoforever.com to the IP.

---

### Post by christoforever on 2009-01-22
To do that, do I have to setup a DNS server on my local machine or can I go through say godaddy.com or another site which has a DNS server?

---

### Post by nishv on 2009-01-22
It has to be done on the DNS Server of the above Domain Name...

Since you are using Godaddy's DNS Servers, you need to login to the DNS Control page and Add it...

---

### Post by christoforever on 2009-01-22
nishv: Thank you, that did it. godaddy does not make doing such a thing exactly easy or intuitive, but after some digging through their site I found where I needed to Add an A record and that worked. Thank you.

---

### Post by nishv on 2009-01-23
Glad I was able to help! :)

---

