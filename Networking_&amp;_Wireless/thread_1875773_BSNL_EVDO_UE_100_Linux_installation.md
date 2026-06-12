---
title: "BSNL EVDO UE 100 Linux installation"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by harry1868 on 2011-11-05
I have bought NEW EVDO , you guys know it is with SIM card (RUIM) inside. I cant configure it with wvdial 
New model is UE 100 which manufactured my Prithy soultions.I was working with old EVDO witout Simmodel  AC 8700 , it was working fine on my Ubuntu 10.04 with out any issue using wvdial .Do you guys have any tips for configuring UE 100 on Ubuntu?
When i hit wvdial .it shows tilll Carrier detected some time ss,,but not getting connected, some time it will show signal not found < but there is no way bcz when sales man come to My home he showed demo on his windows PC with Full coverage.so there is no chance of no covergae.
i hit 
wvdialconf and genertaed new /etc/wvdial.conf 
the device detected on /devttyACM0
dial number is #777
Any idea ? any one configured succesfull UE100 on ubuntu?

---

### Post by harry1868 on 2011-11-07
anyone? help plz i am still stuck

---

### Post by harry1868 on 2011-11-07
First EVDO AC8700 was not working just by inserting, i installed wvdial pacakge.then edited wvdial.conf
just username and password only. at that time it was detected on /dev/ttyusb0

Then recently i changed it to UE100 new model from bsnl.it is model  with RUIM sim , old model was with out sim.
 But it wont work by simply editing wvdial.conf .
I found the problem was due to /dev/ttyusb0 on wvdial.conf , new model was not detected on /dev/ttyusb0.
So i run wvdialconf command , it automatically created /etc/wvdial.conf . Now the device detected on /dev/ttyACM0,

To my surprise the username and pasword i entered manually before hitting wvdialconf command remains same after wvdialconf command too.dialing num #777 itself.


Now the issue is when i use command sudo wvdial  
it hangs by waiting for carrier line only ..

There are no line of ppp

---

