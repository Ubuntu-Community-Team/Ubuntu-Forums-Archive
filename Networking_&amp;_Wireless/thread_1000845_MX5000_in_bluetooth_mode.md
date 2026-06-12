---
title: "MX5000 in bluetooth mode"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by Jabone on 2008-12-03
Hey Guys!

I'm having issues with Logitech MX5000 combination. 
Mouse and keyboard works but in HID mode. I want the receiver to bluetooth mode so that I can hook up my phone with it. 

I've searched forums for solution but nothing yet. 

hcitool dev gives me no adapters and bluetooth icon does not appear. 

I tried hid2hci thing but nothing. 

Any help please

EDIT:

I succeeded in switching receiver to hci mode. Trick was to command
hciconfig hci0 down and
hciconfig hci0 up

Then I had to connect keyboard and mouse with hidd 

Anyway bluetooth icon does not appear and I cannot pair my nokia:-(

---

