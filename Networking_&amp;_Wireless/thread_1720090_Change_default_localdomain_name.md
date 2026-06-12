---
title: "Change default localdomain name?"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by jleg94 on 2011-04-02
Does anyone know how to change the default localdomain from .local to .somethingelse? I have tried changing the "kernel.domain" option in /etc/sysctl.conf and I have also tried using the "domainname" command and neither has seemed to work (still appears to be hostname.local on other computers within the LAN). Any ideas?

---

### Post by moejay on 2011-04-02
I think you need to set up a dns to do that, 

I recommend using bind

---

### Post by jleg94 on 2011-04-02
I forgot to mention, setting up a DNS is not an option. Is there any other possible way?

---

### Post by moejay on 2011-04-02
dhclient sends hostname, so I'm thinking there's an option that allow u to do that sort of thing, 
a quick look at "/etc/dhcp3/dhclient.conf"  shows an option "supersede domain-name"
Unfortunatley i have a dns, and right now i have a 3g problem am working on, or else i would have done some testing ....

---

### Post by jleg94 on 2011-04-02
Thanks for the information, I didn't know dhcpclient handled that. I'll give it a try.

---

