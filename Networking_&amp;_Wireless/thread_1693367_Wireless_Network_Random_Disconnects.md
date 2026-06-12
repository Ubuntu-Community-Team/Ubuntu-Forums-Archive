---
title: "Wireless Network Random Disconnects?"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by artsim2011 on 2011-02-22
I've had ubuntu installed for a bit now and I want to start using it as my main OS, but the wireless internet will not stay connected. It will connect at first and if I'm lucky it will stay connected for around 15 - 20 minutes. I have a toshiba laptop with an AtherosAR5007EG internal network card if you want more information please let me know.

---

### Post by uncaspi on 2011-02-23
Try to quit power save mode.

sudo iwconfig wlan0 power off (assuming your card is wlan0)

and increase transmit power

sudo iwconfig wlan0 txpower 20

---

### Post by artsim2011 on 2011-02-24
Well I just tried the two commands and the command to turn off power saver mode gave up an error:
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
and the second command seemed to have worked so we'll see from here. Thank you so much for replying I hope that this fixes my problem.

---

