---
title: "Netear WG111T usb wireless dongle"
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by KB3MKD on 2006-02-09
It doesn't seem to work using the built in Atheros diver.

Trying ndiswrapper shows 2 drivers required.  1 shows up as driver installed, the other as driver installed, but hardware not present.

I'm looking for any way to get this thing working.

Scott

---

### Post by KB3MKD on 2006-02-09
more info

results of ndiswrapper -l

athfmwdl                driver installed, hardware present
netwg11t                driver installed

---

### Post by KB3MKD on 2006-02-10
Why would the system se one device, but not the other?

---

### Post by KB3MKD on 2006-02-12
IT WORKS!!

I had to load ndiswrapper v1.10 from source, but it works!

---

### Post by aircool on 2006-10-07
could you please instruct me on how you got it to work thanks

msn me or something plz

Ben

---

