---
title: "Need to share printer to a Vista laptop from my Ubuntu desktop."
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by JayRott on 2009-05-12
Ok I need some help sharing my hp printer. I use 9.04 on my main computer and the printer is connected to it. My wife uses vista (ugh!) on her laptop, and we are connected via wireless router. I installed samba but I don't know where to go from there. please break this down for me as simply as possible and I will be GREATLY appreciative. Thank you. everything I have seen so far has been the other way around.

---

### Post by puppywhacker on 2009-05-13
I thought Samba shares printers by default to spool to cupsd, so you should be good to go. On the vista machine just add a network printer.

if needed place the drivers in /var/lib/samba/printers

/etc/samba/smb.conf
```
printer
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

```

---

### Post by JayRott on 2009-05-13
> **puppywhacker said:**
> 

if needed place the drivers in /var/lib/samba/printers


I'm not sure how to do that. I did add the code to /etc/samba/smb.conf but that didn't get me anywhere. I really need vista and Ubuntu to play nice.

---

