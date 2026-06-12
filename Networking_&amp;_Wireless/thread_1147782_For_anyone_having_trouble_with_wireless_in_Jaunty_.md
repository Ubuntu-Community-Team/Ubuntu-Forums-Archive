---
title: "For anyone having trouble with wireless in Jaunty on Acer Aspire One"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by Sims12345 on 2009-05-03
I found this workaround [URL="https://bugs.launchpad.net/ubuntu/+bug/350352"]here
[/URL]
> 

I have this working by doing the following:

1: Add the following lines to /etc/modprobe.d/blacklist.conf

blacklist ath_pci
blacklist ath_hal
blacklist acer_wmi

2: Add the following line to /etc/modules

ath5k

3: Install the linux-backports to get the latest ath5k driver

sudo apt-get install linux-backports-modules-jaunty

4: Remove any currently installed modules

modprobe -r ath5k acer_wmi ath_pci ath_hal

5: Install the ath5k modules

modprobe ath5k

At this point you should be good to go.


Hopefully this helps someone

---

### Post by Chiapo on 2009-05-18
Unfortunately, the Acer Aspire One has "Wireless Broadband" (aka HSDPA/3G/UMTS/etc) along with WiFi.
I'm currently unable to connect using the AAO internal 3G modem.
My (somewhat haphazard) research points to running the Acer 3G Connection Manager through wine in order to get "Wireless Broadband" connectivity in Ubuntu.
That, or writing an application that runs native in Ubuntu.

---

### Post by Sims12345 on 2009-05-18
Mine only has wifi, no 3G...

---

### Post by meeples on 2009-05-18
> **Chiapo said:**
> Unfortunately, the Acer Aspire One has "Wireless Broadband" (aka HSDPA/3G/UMTS/etc) along with WiFi.
I'm currently unable to connect using the AAO internal 3G modem.
My (somewhat haphazard) research points to running the Acer 3G Connection Manager through wine in order to get "Wireless Broadband" connectivity in Ubuntu.
That, or writing an application that runs native in Ubuntu.

i know theres a linux app that vodafone's Betavine make for using 3g, but i'd imagine it would only work if you were on vodafone...

[https://forge.betavine.net/frs/?group_id=12]("https://forge.betavine.net/frs/?group_id=12")

---

