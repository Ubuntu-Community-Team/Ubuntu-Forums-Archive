---
title: "Wicd reconnect problem, WEP key issue?"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by rrwood on 2009-03-27
I have a server install of Ubuntu 8.10 working mostly well on an HP Mini netbook.  I'm using Wicd to manage wireless, and it works quite nicely to establish the initial connection to my wifi router.  Unfortunately, if I attempt to reconnect to the router after booting, things don't work so well.

Looking at the /var/log/wicd/wicd.log, I can see that Wicd is doing all of the usual stuff to bring up the connection, but it just never gets assigned an IP by the router.  The real gotcha is that if I use iwconfig to set the WEP key while Wicd is attempting to connect to the router, things do work.

Anyone have any insights here?

As mentioned, Wicd works perfectly well the first time I connect to my router, but subsequent connections fail because the WEP key seems to not be set.  

And yes, the config in /usr/lib/wicd/configurations contains the WEP key as expected.  My WEP key is 128 bits (26 chars), and is correctly specified in the wpa_supplicant config file in /usr/lib/wicd/configurations.  The wpa_supplicant docs seem a little sketchy on 128 bit keys, but it all works the first time after boot, so I know it's good.

Thoughts, people?

---

### Post by GavinZac on 2011-04-26
I'm having this exact issue in 10.10. I'm only using wicd because I wanted a static IP address on my network.

It will pass the WEP key check, saying 'validating authentication', before moving on.

If I have static IP enabled, it will say 'verifying access point asociation'; if I do not, it will say 'obtaining IP address'.

Finally: 'Error connection failed: could not contact the access point.'

---

### Post by AggravatedGestalt on 2011-04-26
I have been trying to get wicd to work with wireless in Ubuntu for almost a year now, and have had no luck. I very much prefer it over NetworkManager, and wish I could use it, but have come to accept it will not work with wireless in Ubuntu,.. at least not for me.

---

