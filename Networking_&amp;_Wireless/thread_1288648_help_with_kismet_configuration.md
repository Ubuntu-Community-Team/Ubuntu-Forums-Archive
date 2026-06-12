---
title: "help with kismet configuration"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by anson123 on 2009-10-11
Hi,

I installed Kismet from the repsitories....and started to configure the kismet.conf file.

I couldn't figure out what to use for my wireless card.

from the lspci command, i have:

Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection

in the kismet readme file, there is no listing for this card.

does anyone know which one, if any, would be compatible?  I'll start trying the different ones listed and see if it works...

thanks for any help!

---

### Post by chili555 on 2009-10-11
You might try:```
iwlagn,wlan0,Intel
```Or else:```
iwlwifi,wlan0,Intel
```Kismet doesn't work with every last card, unfortunately.

---

### Post by anson123 on 2009-10-11
i have tried to use the iwl4965.....but can't seem to get kismet to even start.  below is the output of the kismet command:

laptop:~$ kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
Done.
laptop:~$

---

### Post by chili555 on 2009-10-11
What does this do for us?```
[COLOR="Red"]sudo[/COLOR] kismet
```Incidentally, my iwl3945 is difficult to get back to Managed mode and connect. Post back if you need help.

---

### Post by anson123 on 2009-10-11
well i guess iwlagn does not work....will try the other one next and post the result.

laptop:~$ sudo kismet
[sudo] password for eelnosna: 
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'iwlagn' in source 'iwlagn,wlan0,Intel'
Done.

---

### Post by anson123 on 2009-10-11
same results with the iwlwifi source type...


laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'iwlwifi' in source 'iwlwifi,wlan0,Intel'
Done.

---

### Post by chili555 on 2009-10-12
This is from the Kismet documentation on their website:> All modern drivers on Linux use the mac80211 driver framework.  Kismet will auto-detect any driver using this framework.  A generic source type 'mac80211' can be used for forcing a type, however it is not strictly useful to do so.
---snip---
      mac80211          Generic mac80211 capture source for any mac80211 drivers.
---snip---
This is a bit of a long shot, but please amend your kismet.conf to use *mac80211* as the capture source. Then do:```
sudo kismet
```Please post the result. The searchers and I will be very interested.

---

### Post by anson123 on 2009-10-13
lol, same results...


laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'mac80211' in source 'mac80211,wlan0,Intel'
Done.

---

### Post by chili555 on 2009-10-13
Well, all we have confirmed is that Kismet doesn't yet work with every wireless card. Sorry. 

If Kismet is important enough to you, you could always consider adding a PCMCIA or USB card. Research carefully before purchase.

---

### Post by deltron30 on 2009-10-13
I get the same issue with the 5100 series card. It says in the readme it is supported. I've tried using every different Intel conf but I still always get this error.

```
FATAL: Unknown capture source type 'iwlwifi' in source 'iwlwifi,wlan0,Intel'
Done.

```

This is what finally worked for me:
```

source=iwl4965,wlan0,test

```

Hope it works out for you.

---

### Post by anson123 on 2009-10-14
ok, that seemed to work for me as well!

Thanks for the help!

---

