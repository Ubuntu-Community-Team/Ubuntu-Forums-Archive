---
title: "no internet thru LAN"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by decrepit on 2011-04-01
Just bought an emachines e528 and installed 10.04.

I have a broadband modem, if I plug that into eth0 using dhcp connection's OK.

The before I got the emachines, I had an old PC (charlie), connected to my main desktop, (percy) with a cross over cable. 
The modem plugged into Percy is maqueraded to charlie.

OK so I've also named the e528 charlie, and connected via crossover to percy, changed eth0 to the correct address instead of dhcp, and expected to get internet access, but it doesn't happen.

Ping works both ways between percy and the new charlie, so the nics are connecting OK. but I can't ping the modem from charlie.

I haven't done anything about a firewall for charlie, could this be the problem?
Or is the different machine name for the new nic confuse things?
I also want to set up samba between them, but I've a feeling that won't work until the internet does.

---

### Post by decrepit on 2011-04-01
Just did a port scan from percy and there's only 2 ports open on charlie, 139 and 445. 

Where as from the other direction percy has 111, 135. 139, 445. 1024, 2049, 33208, 40427 and 40724.
Not sure how relevant this is, just playing around, trying to find something that works.

---

### Post by decrepit on 2011-04-02
Interesting, I've got samba working, but still no internet.
Anybody got any clues???

Woops, no samba is only half working, charlie can see percy but percy can't see charlie.
percy appears on both computers but charlie appears on neither.

---

### Post by decrepit on 2011-04-03
OK everybody can relax, the internet's fixed.

Just had to add percy's address in "gateway". That let me ping the modem.
Then added the modem's address into "DNS server".

Still can't open charlie's shares though.
The "share files", thing keeps returning an error, can't use the folder name, that's already used, and every other name translates as "everyone", which it also won't do.

---

