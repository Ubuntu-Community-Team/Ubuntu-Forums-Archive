---
title: "Wireless NC10 with Jaunty"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by PaulHeywood on 2009-05-08
Hi there - I've a fresh install of 9.04 Xubuntu on a Samsung NC10 and for the life of me I can't get the wireless to work - previous versions of Ubuntu have been ok.

I've followed the instructions here ([https://help.ubuntu.com/community/NC10#Wireless](https://help.ubuntu.com/community/NC10#Wireless) Networking - Atheros) but still no joy...

The networkManager applet has the Wireless Networks greyed out.

Not sure going back to intrepid would help....

---

### Post by chili555 on 2009-05-08
Does it spring to life if you do:```
sudo modprobe ath5k
```

---

### Post by PaulHeywood on 2009-05-08
Thanks for the response, it didn't spring into life sadly, it warned about "All config files need .conf:...." but still no wireless

---

### Post by chili555 on 2009-05-08
> it warned about "All config files need .confThat's fairly trivial and not hard to fix, but let's see if we can get the wireless going first. Please post:```
iwconfig
```Thanks.

---

### Post by PaulHeywood on 2009-05-08
I'd been using my xp partition while I hoped for responses - as soon as I rebooted back into Ubuntu the wireless was up straight away - not sure why but thanks very much for the response.

---

