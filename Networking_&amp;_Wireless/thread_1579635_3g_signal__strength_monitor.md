---
title: "3g signal  strength monitor"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by b-boy on 2010-09-22
Hi

I am looking for a tool that can monitor my 3g sinal

---

### Post by TNT1 on 2010-09-22
I'm sure wicd shows RSSI...

Wait, maybe only wicd 2.0 and I don't know if that's released yet.

---

### Post by b-boy on 2010-09-22
wicd is pretty much what i am looking for but it does not support 3g network

---

### Post by TNT1 on 2010-09-22
This is one way to do it:

1. Install terminal program cu : sudo apt-get install cu

2. Connect to the modem : cu -l /dev/ttyUSB0
  - this may be also ttyUSB1, 2 or bigger, depending on your modem

3. Give AT command to check the signal : at+csq
- this gives you the RSSI, see further below

Notice:
- Exit cu by keys: "~" and "." (Ctrl+C or else do not work) 
- Some modems work with the connection on, some do not, so it may be wise to disconnect from internet before trying cu.

From: [http://www.uluga.ubuntuforums.org/showthread.php?p=9149241](http://www.uluga.ubuntuforums.org/showthread.php?p=9149241)

The table [http://www.siptune.net/tiki-index.ph...Signaalinaytot]("http://www.siptune.net/tiki-index.php?page=Signaalinaytot")  helps you realize the RSSI (Radio Signal Strength Index) compared to  other indicators of signal strength. (The table headings are in Finnish,  but it is very easy to figure out.)

---

### Post by TNT1 on 2010-09-22
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8597531](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8597531)

---

### Post by mbuotidem on 2010-09-22
i know what you need. IXCONN. get it here: [http://mwconn.m.i24.cc/ixconn.deb](http://mwconn.m.i24.cc/ixconn.deb).

If you need any help check the manual.

---

### Post by b-boy on 2010-09-22
ixconn does not support 64 bit

---

