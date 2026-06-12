---
title: "hello guys , please help"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by mzunguu on 2011-01-23
Hi , i have recently moved to germany , and a friend i live with is using dsl modem connection trough service called Alice dsl-de. , i could see however that ,on her own laptop (windows7) she uses dial up connection with router. , and according to that i have tried to connect my ubuntu10.04 , either trough newly created dsl connection (but it still uses normal rj45 cable) or even trough new mobile connection , nothing works , does anyone has same problem , and knows already how to's ? as said , i have local network with flat router , but it doestn let me connect to internet , as on widnows it uses dial up connection to Alice provider (her plsn id Alice light max flat). have tried to contact website help , but no answer so far .
vlasta
thank you in advance

---

### Post by dandnsmith on 2011-01-23
I'm not sure exactly what configuration you're trying to get working, but have a thought for you:
Did you know that, in Germany, the standard for DSL work is DSL over ISDN, not like in the UK. You need a special modem/router equipped to handle this - most of the UK ones won't.

---

### Post by mzunguu on 2011-01-23
hi , well yeah , it has like normal phone line in a wall .., and from there is dsl cabel connected to sort of router from the company provider ,
and from router is cat5 cable going out for internet.
but connection allows me only local network. ,to enter internet , writes me in windows laptop ,uses device PPPoE ,and server type PPP . ,so at the moment i'm lost, but it should have smtng with connection type as you have mentioned .,will look at it later on. thanx anyway derek .\
vlasta

---

### Post by dandnsmith on 2011-01-24
I haven't ever looked at a setup in Germany - the info I got was from another forum, which didn't go into usage (merely that the organisation was different).

In the past my wife had a connection (in the UK) for company work over ISDN. That modem had 2 outlets on the user side, one to plug in a normal telephone, the other for a PC ethernet cable. A sort of dialup was used which only connected to her company, and I could never get to the level of connection with the modem which would enable me to probe it properly. I did, however, get the feeling that it was tied to connect to only one point at the far end, and if they didn't allow internet access (hers did) you just wouldn't get there.


HTH

---

### Post by tejas.deshpande on 2011-01-24
Well, I could suggest something, but thats not ubuntu side, its the router side.

Well, first you need to get onto windows 7 and connect to the internet through the router. 

Now open the browser, and type in the IP address of the router (by default it should be 192.168.1.1).

Now head over to the WAN section. In there use PPP, enter the userid and password that the ISP provided you, and set the connection as always on. (This procedure will vary from ISP to ISP and Router to Router)


Now, if ubuntu gets onto Auto eth0 then you should be able to connect to the internet.

UPDATE : If you are comfortable with commandline, then I suggest using sudo pppoeconf. 


There is another way of configuring ubuntu, without playing around with the router settings, though I do not remember clearly, something to do with setting up a new wired connection as DSL and entering your ISP userid and password.

---

### Post by mips on 2011-01-24
Easiest way to fix this is to connect to the router, take it out of bridged mode and put it into routed mode and enter her username & password. Should be under the wan settings.

This will allow the router to do the authentication. Both PCs only need to get an IP address via dhcp from the router to work and you can ignore the PPPoE dialer.

As her first though as this is her service before you change anything on the router.

ATM Protocol: PPPoE LLC	
VPI: 1
VCI:32
MTU & MRU: 1454
Username must be specified WITHOUT "@hansenet.de"

What make and model router is she using?
[http://patraulea.com/hacks/alice-router-shell/](http://patraulea.com/hacks/alice-router-shell/)
[http://www.toytowngermany.com/lofi/index.php/t54109.html](http://www.toytowngermany.com/lofi/index.php/t54109.html)
[http://www.dsl-magazin.de/forum/board-alice-dsl/thread-alice-dsl-und-router-8739-page-1.html](http://www.dsl-magazin.de/forum/board-alice-dsl/thread-alice-dsl-und-router-8739-page-1.html)

[http://www.dl-support.de/forum/viewtopic.php?t=3667](http://www.dl-support.de/forum/viewtopic.php?t=3667)
> 

Provider: Hansenet 
Attention: Hansenet are different regional settings required! 

MTU and MRU value: 1492 
Support: [http://www.alice-dsl.de/opencms/export/de/service_res/hilfe/](http://www.alice-dsl.de/opencms/export/de/service_res/hilfe/) 
Alice tutorials: [http://www.alice-dsl.de/opencms/export/de/service_res/hilfe/anleitungen/](http://www.alice-dsl.de/opencms/export/de/service_res/hilfe/anleitungen/) 
ISP settings / router connection data: 
Username: [email]Benutzername@hansenet.de[/email] 
Password: from Hansenet (if you have no password then give Alice a) 

VPI: 8 
VCI: 35 

or: 

VPI: 1 
VCI: 32 

MMOD Enable: When high-speed device 

From HanseNet Support: 

Should support your DSL modem / router the so-called UR2 standard, an operating the DSL port is possible. 
Without their own modem router can be connected directly to the modem supplied by Alice. 

The general settings are: 

VPI / VCI: 1 / 32. 
MTU: 1492 
Protocol: PPPoE 
Connection Type: PPPoE LLC 
Authentication: CHAP 
WAN IP is assigned dynamically 
The access information related to your cover letter must also be stored in the router. If your router is on the entry of a password can 
You enter "1234". 

Our DNS servers are: 
name1: 213.191.74.18 
name2: 213.191.74.19 
name3: 213.191.92.87 
name4: 213.191.92.86 
name5: 213.191.74.11 
name6: 213.191.92.84 
name7: 213.191.74.12 
name8: 213.191.92.82 

Please always use the pairs name1 / 3, name2 / 4, name5 / 7, name6 / 8 

Alice-DSL has since started his user ID 04/01/2007 to change. 

This was before: "Tel.No. of users, including area code" @ alice-dsl.de (example: 012 388 866 633 (at) alice-dsl.de) 

If this code does not work then they take ONLY the "Tel.nr. of users, including area code, minus the Annex Example: 01238886633
[http://forum.dlink.de/topic.asp?ARCHIVE=true&TOPIC_ID=36054](http://forum.dlink.de/topic.asp?ARCHIVE=true&TOPIC_ID=36054)

---

### Post by mzunguu on 2011-01-24
hi , thank you .., i have done so , i went in router trough browser , there is very basic user interface , but i found that internet connection tarif , is being automatic and always on .,as it was all the time , will reset settings to default and config. those again myself ,
after that i'll try .. again . , thank you ,
if i will encounter same trouble i will try reconfigure in my laptotp dsl connections. , but that was point where i stopped before , i have all credentials to paste in , but when i add new dsl connection it doesnt react at any inputs. 

however at the connecting  to modem trough rj45 cable(internet) link is active cca 1-3kb a minute or so ..

---

