---
title: "Mobile Broadband - what's happening here?"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by frankwakeman on 2009-08-31
I had a little random experiment yesterday wth Ubuntu, using my modem to connect to the O2 and Vodafone equivalents of the 3*** that I actually have, i.e. using Ubuntu's built in settings for most of the UK Mobile Broadband networks, and with OpenDNS settings for both.  It did connect, and pages could be read.

I'm wondering what happened there, whether it just connected to 3 anyway, despite different APN and password etc, or whether there's a flaw with Ubuntu's Network Manager.  And if did connect to three, why is it important to have the right APN etc?



*** 3, a UK mobile phone/broadband company

---

### Post by GeorgeVita on 2009-08-31
Hi **frankwakeman**,
APN is needed by 'specification'. Some providers do not use it as they have one option for mobile broadband. Others have more than one profile for their customers and if you choose the wrong one ... it will cost you!

Ex.: my provider has a 'low cost' internet browsing for 4 Euros per month and can be used from prepaid accounts with smart phones. Sometimes you can use these phones as a 3G modem. If you setup the 'real internet' instead of the 'low cost' your first 1-2 minutes browsing will cost 25-30 Euros (I have already paid a 'test' in the past!).

So for your case the most possible is that your account accepts 'other' APNs or just your provider accepts any APN or finally the default APN stored into your SIM is always used.

Regards,
George

---

