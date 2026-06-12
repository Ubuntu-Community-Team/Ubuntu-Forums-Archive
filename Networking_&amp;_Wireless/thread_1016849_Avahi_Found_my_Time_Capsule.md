---
title: "Avahi Found my Time Capsule"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by Oldan on 2008-12-20
** Work around found **
I must be the only person in the world doing this. I can't find anything on any thread about it...

I have a Time Capsule - I bought it to help my mother configure hers. I thought it was kind of cute so I kept it. Now I'm trying to use it. I have a printer connected to it. when I use Avahi to browse for printers, it responds that the printer is available and gets all the right data (even the name) **EXCEPT** the IP address for the device is showing up as 169.x.x.x.

As a result, the printer never works. Even if I change the configured printer to the right IP address, it still doesn't get the printout!

```
Location of the network printer
host: 169.254.207.154
Port Number: 9100
```

Anyone have any clues how to configure the Time Capsule so it'll work with Avahi/Ubuntu?
thanks,
Oldan

---

### Post by Oldan on 2008-12-27
By changing the host IP address to the real address and using HP4 PRD driver, it works. Sort of.

-- Oldan

---

