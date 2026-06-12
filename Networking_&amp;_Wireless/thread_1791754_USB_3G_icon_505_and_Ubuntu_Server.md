---
title: "USB 3G icon 505 and Ubuntu Server"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by tntteam on 2011-06-27
Hi,

I'd like to plug an icon 505 to my ubuntu server 11.04 and send SMS using it (nn www access, only sms send).

I tried many things, but every tutorial points to dead links or old distros or old icon usb key models.

I'm loosing my hair on this, any help would be much appreciated.

Thanks

---

### Post by tntteam on 2011-06-27
Anyone interested :

First, check that the sim card you got from ur local reseller is abble to send SMS ! Ok sounds idiot but I lost 3 hours searching why the usb stick won't send sms when it was only because of this stupid guy that lend me a "not abble to send sms" sim card...

Anyway.

Install gsm-utils package and send sms using

gsmsendsms -d /dev/ttyHS2 06xxxxx 'Message'

U may have to adapt the -d to reflect the correct device for you.

---

