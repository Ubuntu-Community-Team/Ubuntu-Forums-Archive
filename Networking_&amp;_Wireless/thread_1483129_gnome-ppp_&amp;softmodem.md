---
title: "gnome-ppp &amp;softmodem"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by ottosykora on 2010-05-14
I have laptop toshiba, with toshiba softmodem. The modem is recognized well by the 10.04, it dials the right number, but then it breaks the communication after some time out due not able to find carrier, or if it finds it, it will loose it immediately again.

OK, I think it is fine that the modem is getting operated at all, but are there any known tricks to get simple DUN working this way?

---

### Post by alexfish on 2010-05-14
hi

here is a site , don't know if it will help

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

regards

alexfish

---

### Post by ottosykora on 2010-05-14
meanwhile did some other tests:

with the build in modem, it might work, but I am getting this in the log:

-> Waiting for carrier.
ATM1L3DT0840555555
CONNECT 37333
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
You are on node Freesurf pop-ls-13-2
Username :
--> Timed out while dialing.  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Fri May 14 17:37:06 2010

This unable run pppd is probably the critical thing. What exactly should I go change? Serach for the pppd and chmod it? Or what exactly?

Then I also tried to use the famous ELSA Microlink USB modem. This I was using with knoppix and other linux and it did work. Unfortunately it seems not to be prperly detected by 10.04, thought it tries, since during the find procedure leds are flashing. Anybody got this one working?

---

### Post by dineshs on 2010-05-14
I think its a permission issue.Pl read
[http://ubuntuforums.org/archive/index.php/t-931872.html](http://ubuntuforums.org/archive/index.php/t-931872.html)
OR
You can try
```
sudo gnome-ppp
```
 in a terminal

---

