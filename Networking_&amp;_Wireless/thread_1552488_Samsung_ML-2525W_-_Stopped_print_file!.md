---
title: "Samsung ML-2525W - Stopped print file!"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by Skyxn3t on 2010-08-13
I installed the following driver from the Samsung website:
**UnifiedLinuxDriver_0.92.tar.gz**
For the printer: Samsung ML 2525W 

Then I went to:
System -> Administration -> Printing -> Add -> Printer
The Network printer was found, so I added the printer: Here's the printer URI:** ipp://192.168.15.125:631/ipp**

Whenever I try print anything the printer icon gets disabled and I get the following message:
[B][COLOR=SeaGreen]"Print error"
"There was a problem sending document 'Document1' (job 54) to the printer"
"Stopped print file!"[/COLOR][/B]
And If I try to enable the printer I get the same message and the printer gets disabled again.

If I go to CUPS: localhost:631 I noticed the following in the status:
[B][COLOR=Blue]pending since
Fri 13 Aug 2010 05:41:40 PM EDT 
"/usr/lib/cups/filter/rastertosamsungspl failed"[/COLOR][/B]

Does anyone know why does this happen, I've been searching Google for 3 days with no use.

CUPS version: 1.4.4

---

### Post by WCW1 on 2011-03-08
I know this is an old message but I thought I would ask since you got no replies to your question. There may be some other members with the same problem.

Did you get it working?

There are three drivers required to make the ML2525 work correctly. They are all posted on Samsung support website.

I don't know if you will even see this reply but I hope you were successful in getting the 2525 to work

WCW

---

