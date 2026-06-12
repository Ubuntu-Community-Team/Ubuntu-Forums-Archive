---
title: "Wireless on PCMCIA card not working"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by Crawlspace on 2010-02-12
I have a Dell Latitude C810 with a D-Link DWL G650 PCMCIA card connected.
 
I have Ubuntu 9.10; Gnome ver 2.28.1 
 
I have installed all the correct drivers etc and can see my wireless router but when trying to connect to the wireless connection and entering my WEP passphrase it seems to think about it for a while and then the passphrase dialogue box pops up again.
 
I have checked through the forums looking for answers but all seem to end up working for the postee but not me!
 
I ran one script that a post showed and it showed my Channel as number 6 on the router. Not sure if this helps but....
 
The script was something like | grep network
 
Anything to try would be gatefully appreciated.
 
:D
 
PS I am new to Ubuntu / Linux!!

---

### Post by gordintoronto on 2010-02-12
You're sure the router is using WEP?  (It shouldn't, it's not secure!)

What do you mean when you say you installed drivers?  I think support for the G650 is built-in.  "It just works...."

---

### Post by chili555 on 2010-02-12
> WEP passphraseI think Network Manager wants WEP in 40/128-bit hex, not password. Did you try that?

---

