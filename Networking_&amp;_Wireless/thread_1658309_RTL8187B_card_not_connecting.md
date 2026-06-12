---
title: "RTL8187B card not connecting"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by Boludinux on 2011-01-02
I had Ubuntu Jaunty installed and my Realtek card RTL8187B from my laptop worked just fine.

Then  I got a cablemodem service which I used with the Ethernet entry at the  same time I installed Lucid so I didn't used the card anymore.

Now Im travelling and I realize the card isn't working (it is working on Windows)
I use WICD to connect and on the connection process it gets to the step where it has to assign my IP and it fails.
dmesg says this

[ 1230.260352] wlan0: direct probe to AP 00:1e:e3:96:b4:8a (try 1)
[ 1230.460062] wlan0: direct probe to AP 00:1e:e3:96:b4:8a (try 2)
[ 1230.660089] wlan0: direct probe to AP 00:1e:e3:96:b4:8a (try 3)
[ 1230.860049] wlan0: direct probe to AP 00:1e:e3:96:b4:8a timed out

I have no idea what to do... I have kernels from 2.6.35-21 to 27 (I think that is the numeration) and none is working.

Any suggestions welcome I don't really want to spend my summer in the always vulnerable XP.

---

