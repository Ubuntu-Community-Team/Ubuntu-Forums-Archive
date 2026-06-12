---
title: "Connection to USB mobile phone/modem won't fully work after wvdial crashed"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by boppis on 2009-01-01
I managed to connect and configure my mobile phone to send sms messages thru minicom. When I tried connecting thru wvdial an error in wvdial.conf (trying to interpret an AT+CMGS command) caused the program to crash and since then messages can't be sent, neither by AT+CMGS nor AT+CMSS. All i get is "+cms error: 304" (error code descriptions: [http://www.developershome.com/sms/resultCodes2.asp#16.2.1.The%20+CMS%20ERROR%20Final%20Result%20Code%20--%20Notifies%20the%20Occurrences%20and%20Causes%20of%20Message%20Service%20Failures|outline](http://www.developershome.com/sms/resultCodes2.asp#16.2.1.The%20+CMS%20ERROR%20Final%20Result%20Code%20--%20Notifies%20the%20Occurrences%20and%20Causes%20of%20Message%20Service%20Failures|outline))

All other AT commands seem to work. I have tried with different phones but the same error occurs, so the problem most likely lies within ubuntu.

I've tried reinstalling both wvdial, minicom and mobile phones as modems without success.

Seems like there's some data stored somewhere in ubuntu that interfers with the AT commands for sending messages, but i have no clue where. Pls help!

---

