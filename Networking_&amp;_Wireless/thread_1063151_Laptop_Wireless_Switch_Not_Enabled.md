---
title: "Laptop Wireless Switch Not Enabled"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by stri8ed on 2009-02-07
First off, complete noob here i just installed ubuntu on my acer 5570z laptop alongside vista.


i did the driver test and it did recognize my network card. but the wirless switch to enable the wireless is not doing anything and stays disabled.


can somebody please give me a step by step process to enable it for a complete beginner with no experience whatsoever.

Many thanks!

---

### Post by stri8ed on 2009-02-07
please?

---

### Post by stri8ed on 2009-02-07
bump

---

### Post by stri8ed on 2009-02-07
anyone

---

### Post by danni-la on 2009-02-07
On my dual boot acer I had a similar problem, I booted in windows to make sure the wireless was actually on (the lights on the switch don't work as yet so this is the only way for me to check it) then rebooted in ubuntu and the network manager sees it as enabled.

Not sure if it helps but worth a try?

Cheers Danni

---

### Post by stri8ed on 2009-02-07
> **danni-la said:**
> On my dual boot acer I had a similar problem, I booted in windows to make sure the wireless was actually on (the lights on the switch don't work as yet so this is the only way for me to check it) then rebooted in ubuntu and the network manager sees it as enabled.

Not sure if it helps but worth a try?

Cheers Danni

When i boot windows its always on, but when i boot from ubuntu it is disabled and the switch does nothing

thanks for the reply though

---

### Post by stri8ed on 2009-02-07
my wireless card is Atheros AR5007EG Wireless Network Adapter

---

### Post by danni-la on 2009-02-07
no probs... have you tried the ath5k drivers from the backports or the madwifi drivers? 

I had to use the ath5k to get mine working.

---

### Post by stri8ed on 2009-02-07
> **danni-la said:**
> no probs... have you tried the ath5k drivers from the backports or the madwifi drivers? 

I had to use the ath5k to get mine working.

no clue what that is, can you give me more info that and instructions for a complete noob?

thanks

---

### Post by racie on 2009-02-07
> **stri8ed said:**
> my wireless card is Atheros AR5007EG Wireless Network Adapter

Ahh, I have the same card and I gave up trying to make it work.  Have you tried [this walkthrough](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)?  It didn't work for me, but it has worked for many others with the same card.  Good luck.

--racie

---

### Post by danni-la on 2009-02-07
> **stri8ed said:**
> no clue what that is, can you give me more info that and instructions for a complete noob?

thanks

to install the backports, copy this into terminal

sudo aptitude install linux-backports-modules-intrepid-generic

I honestly don't know if it will work for you my wireless card is a different model but is Atheros.

after installing I also had to go into the hardware drivers and deactivate the 'support for Atheros 802 etc' driver and only have the 'support for 5xxx series etc' driver activated.

the madwifi drivers can be found here... [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) 

they didn't work for me.

Cheers Danni

---

### Post by stri8ed on 2009-02-07
> **racie said:**
> Ahh, I have the same card and I gave up trying to make it work.  Have you tried [this walkthrough](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)?  It didn't work for me, but it has worked for many others with the same card.  Good luck.

--racie

will try but it appears the link is down, is that cause i running in vista?

[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

---

### Post by racie on 2009-02-07
> **stri8ed said:**
> will try but it appears the link is down, is that cause i running in vista?

[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

Were you talking about the link that I gave?  If so, I don't know what the problem was.  I have Vista also...  the url is:

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

