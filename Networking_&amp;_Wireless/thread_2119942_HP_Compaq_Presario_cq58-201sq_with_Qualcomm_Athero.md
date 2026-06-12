---
title: "HP Compaq Presario cq58-201sq with Qualcomm Atheros QCA9565 card."
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by solotm on 2013-02-25
I would like to know how I can connect to internet in ubuntu 12.10, so fail .... I searched and so far have not found anything that can help me.Can you answer to me please. I think it should be activated first wireless card, mine is 802 .. Qualcomm Atheros QCA9565 Laptop: HP Compaq Presario cq58-201sq. If you can help me please .. Thanks in advance.

---

### Post by chili555 on 2013-02-25
Please open a terminal and run this command:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Is your device identified as 168c:0036? If so, please get a temporary wired ethernet connection and do:```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2
tar -xf compat-wireless-3.6.8-1-snpc.tar.bz2
cd compat-wireless-3.6.8-1-snpc
./scripts/driver-select ath
sudo su
make
make install
modprobe ath9k
exit
```Your wireless should now be working. Post back if you get stuck or if 168c:0036 is not your device.

---

### Post by solotm on 2013-02-26
Thank you, but doesn't work...
The last solution that I found  is to install ubuntu 13.04, and is perfect.
The wifi connection is now working.
Thank you for you have tried..

---

### Post by mörgæs on 2013-02-26
Good, then please mark the thread 'solved'.

---

### Post by solotm on 2013-03-05
I choose Ubuntu ..13.04

and how to make it "SOLVED" ?

---

### Post by mörgæs on 2013-03-05
Hehe - in the mean time the forum has been upgraded, and now the functionality does not work as intended.
I have done it for you.

---

