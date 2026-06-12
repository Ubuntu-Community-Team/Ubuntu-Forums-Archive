---
title: "Configure Ekiga for Vyke SIP provider"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by manosx on 2009-07-08
To connect with Ekiga to vyke sip provider you need to configure an account in ekiga as follows:

Name: [your username] (normally your phone number)
Registar: sip.vyke.com
User: [your username]
Authentication User: [your username]
Timeout: 3600
[&#10003;] Enable Account

In Ekiga Preferences(Edit->Preferences):
In Protocol->SIP Settings
Outbound Proxy: sip.vyke.com

Send DTMF as: RFC2833

And in the Preferences again:
In Audio->Codecs
select only the PCMU codec

When there are also other codecs selected I cannot make any phone calls..
It also seems like the configuration is a bit tricky. Many times you need to restart ekiga to use the new configuration.
Ekiga Version: 3.2.0-0ubuntu1

---

