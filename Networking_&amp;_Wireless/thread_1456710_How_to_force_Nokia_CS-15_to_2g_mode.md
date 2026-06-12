---
title: "How to force Nokia CS-15 to 2g mode?"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by jtbo on 2010-04-17
As it reads, sysconfig is not supported, using wvdial and everything else works perfectly but as living on edge of 3g coverage stick constantly jumps between 3g and edge making 5-10 seconds pauses and disrupting downloads etc. There is no speed difference in my situation and I just need to say that thing that stay 2g.

No AT commands known to Google are working and Google does not know commands of CS-15, nokia site says "we are making list of commands", so no help from there.

I would of paste available commands what modem lists here, but ctrl+c, right mouse button or top left corner of putty did not give me option to copy selected text...
Oh and I have no idea what those commands listed by modem do, who knows if it even explodes or calls to russia when I test them random...

Oh, 2gonly option for wvdial does absolutely nothing.

I'm using Xubuntu 64-bit

edit:
PS. What's wrong with forum search, it did not found anything about Nokia CS-15 and now as I tested again it did not found even this thread?

---

### Post by alexfish on 2010-04-18
hi

These are commands I have found to date ,so I don't know if will will help here



  	 	 	 	 	 	  AT+COPS?
 Will return an additional value:
 +COPS: 0,0,”Vodafone UK”,0


 The digit at the end shows if the card is registered on a GPRS or a UMTS network. (0 == GPRS, 2 == UMTS).
 There is a very useful command that changes the way the V3G card behaves:
 AT_OPSYS=n
 

[FONT=monospace]AT_OPSYS=0      #Only connect to GSM networks[/FONT]
[FONT=monospace]AT_OPSYS=1     #Only connect to UMTS networks[/FONT]
[FONT=monospace]AT_OPSYS=2     #If you have a choice -  GPRS first[/FONT]
[FONT=monospace]AT_OPSYS=3      #If you have a choice – UMTS first[/FONT]
[FONT=monospace]AT_OPSYS=4     #Which ever network you  connect to stay with it.[/FONT]
[FONT=monospace]AT_OPSYS=5      #Automatic – let V3G decide

source

[/FONT]http://www.pharscape.org/vodafone-3g-umts-how-to.html


pharscape also have a forum ,so maybe worth a visit

regards 

alexfish

---

### Post by jtbo on 2010-04-18
Thx, Alexfish, must test that AT_OPSYS when download of Rigs Of Rods finishes. 

AT+COPS with any parameters gives only error from my memory, not even AT+COPS? seemed to work yesterday when I did some testing, must check if it was in list of commands which was possible to get with some AT command. 

Report follows later...

---

