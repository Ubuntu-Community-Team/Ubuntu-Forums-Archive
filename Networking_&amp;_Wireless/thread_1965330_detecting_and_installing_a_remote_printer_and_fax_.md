---
title: "detecting and installing a remote printer and fax device"
date: 2012-04-25
forum: Networking &amp; Wireless
---

### Post by kyosaku on 2012-04-25
Hi there,
 

please help me as I am close to giving up again - is the following really unsolvable ?



so here is my setup:


a HP8500 A910 all-in-one printer @my workplace 

<->connected to a router with a dyndns adress


I can access the printers Embedded Web Server from outside (@home).



I have already configured remote printing by adding a portforward for 9100 in my router and having added a new printer using the command

sudo system-config-printer 


-> adding printer by:  

device URI  socket://dyndnsadress.org:9100



printing a testpage worked out fine :guitar:




Now I tried doing the same thing for the FAX part of my all-in-one, installing FAX4-HPCUPS printer

&adding device by URI socket://dyndnsadress.org:9100
 

but here obviously, sending a testpage did not produce the desired outcome of sending a fax -  pages came out of the printer instead and all with just one letter printed :( - 

ok you'll say, that was to be expected not to work ...

So on I went to use hpsetup, trying to see if this would install the remote device using the network adress

[http://dyndnsadress.org:9100](http://dyndnsadress.org:9100) 

I've also tried  :631 - 

but to no avail: no device detected, not even a printer.
 


 So my question is: what do I need to do for hpsetup or generally my Ubuntu 11.10 to be able to detect and succesfully install/adress/use this remote device, connected to a router@work ?



Do I have to use and configure another port ?  Is there some additional router configuration-work to be done ? Or am I asking too much again and this thing really is unsolvable without using remoteview on a local machine being directly connected to the printer  ?

I would be glad for any input or enlightenment on this !

---

### Post by kyosaku on 2012-04-29
Does anyone have an idea or suggestion ?  
:confused:

Or is installing a remote fax device on a router something ubuntu/hplip isn't designed to be able to do  ?
Am I not getting something here ?

---

