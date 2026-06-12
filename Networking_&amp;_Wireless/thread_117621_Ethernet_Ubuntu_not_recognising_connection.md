---
title: "Ethernet: Ubuntu not recognising connection"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by Dave91 on 2006-01-15
Hi all,

I currently have A Creative Broadband Blaster 8133u modem.

I have it installed on a Windows XP machine. i then have an Ethernet Cable connected to the modem and to my Ubuntu machine. Only thing is that Ubuntu isnt recognising the connection. I need help lol

I Also would like to say that i love the Ubuntu OS but i lack in Linux common sense so please spell things out for me lol

Thanks all :D

Dave

---

### Post by Dave91 on 2006-01-15
OK i found an answer thanks to this:
[QUOTE=adwait]What kind of internet do you have?? If you have xDSL running on PPPoE, this could help:
```
sudo pppoeconf
```

If you have dial up, try gppp.[/QUOTE]


But i got an error message saying basically that a scan failed and it could be because another process is using PPOE; does this mean i must shut down the internet computer when installing the ethernet  on ubuntu??

Thanks all
Dave

---

### Post by Dave91 on 2006-01-15
i feel like a professional Ubutu user, i got it sorted on my own lol :D :D

I had to edit the properties of the network and set them to DHCP :D :D

Now all is good 

Thanks all anyway :)

Dave

---

