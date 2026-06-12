---
title: "Installing printer from another computer"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by Rlad78 on 2009-03-10
First of all, I want to tell everyone who's reading this that I'm a complete Ubuntu noob. 

So I'm having problems connecting to my HP LaserJet 4000 printer that I'm sharing from my other computer (Windows XP). I go to System>Administration>Printing, but when I look at the titlebar, it reads:

Printer configuration - localhost
which is not the name of my host (computerroom)

However, when I try to change the host name, it keeps giving me this error:

There was an error during the CUPS
operation: 'httpConnectionEncrypt failed'.

And whenever I try to create a new printer on localhost, it never works. This could also could be because the new printer setup steps are a little confusing to me...

Does anyone know what I'm doing wrong?

---

### Post by lindsay7 on 2009-03-11
It really not hard at all.

Make sure that the computer that is connected to the printer is on and its OS is running and the firewall is off. Also make sure the fire wall Like Firestarter (Ubuntu computer is switched off too),

Go to Systems/administration/printing, choose NEW (box), it will search, then under (devices) go down to,Windows Printers Via Samba, a text box will open on the right called smb printers, click Browser and it will search. It should find you workgroup or network, clik on that and it will find the "user computer". click on that and it will find the printer. them choose and set the print driver.

That is it.

---

### Post by Rlad78 on 2009-03-11
> **lindsay7 said:**
> it really not hard at all.

Make sure that the computer that is connected to the printer is on and its os is running and the firewall is off. Also make sure the fire wall like firestarter (ubuntu computer is switched off too),

go to systems/administration/printing, choose new (box), it will search, then under (devices) go down to,windows printers via samba, a text box will open on the right called smb printers, click browser and it will search. It should find you workgroup or network, clik on that and it will find the "user computer". Click on that and it will find the printer. Them choose and set the print driver.

That is it.

thank you sooooo much!!

---

