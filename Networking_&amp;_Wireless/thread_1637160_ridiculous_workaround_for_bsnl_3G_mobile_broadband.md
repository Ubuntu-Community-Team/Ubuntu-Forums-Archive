---
title: "ridiculous workaround for bsnl 3G mobile broadband"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by nagaraj on 2010-12-04
had seen lot of posts querying how-to when i was trying to get my bsnl 3G datacard configured on ubuntu -maverick. later on i too faced similar problem. initially the datacard was recognised but after a couple of days the comp( and my laptop - both maverick) failed to recognise the datacard. i tried various things but what worked for me is something rather amusing. if anybody is still stuck with the problem, they too can try that. atleast it wont harm. here is what i did.
i first deleted the 'bsnl broadband connection' from the list of available 'mobile broadband' using network manager.
connected the 'bsnl 3G usb modem'
ejected the usb device by right clicking on the bsnl icon (which appears once the device is mounted)on desktop but keeping the device attatchd
started the network manager> mobile broadband > add
the wizard started and i choose 'india'>'airtel' (YES IT IS AIRTEL-NOT A TYPO !)
i ticked 'connect automatically'and completed the wizard
this created a connection called 'airtel'
then i did - left click on the connectionmanager showed 'airtel' under mobile broadband as available!
clicked on that - network manager worked for sometime and returned 'airtel connected !!'. but obviously i was not able to browse anything.
then i opened the network manager> mobile broadband> airtel > edit 
changed the APN settings to 'bsnlsouth', saved and closed.
reconnected using network manager - bingo, connection worked fine. only it keeps showing the connection as 'airtel'. but what of it? as long as it works.
(i m not a technical man and i dont know what the problem is and why the ridiculous work around works - but i am happy it worked).

---

