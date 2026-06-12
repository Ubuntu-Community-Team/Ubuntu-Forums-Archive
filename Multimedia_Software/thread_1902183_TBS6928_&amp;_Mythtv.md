---
title: "TBS6928 &amp; Mythtv"
date: 2011-12-30
forum: Multimedia Software
---

### Post by kamolt on 2011-12-30
I installed a TBS6928 card in a Ubuntu 11.10 machine. Further I installed the Linux driver as described.
sudo make && make install produced errors and did not work.
However :
$sudo make
$sudo make install
separately did the job. the dmesg command listed the tbs6928 card and tbsci so i assume the driver was installed properly.
dmesg showed also tbs6922fe : module license ''Turbosight Proprietary: [http://www.tbs.com](http://www.tbs.com)' taints kernel (something to worry?)
Mythtv recognizes the tuner card as /dev/dvb/adapter2/frontend0 but fails to find any channels. In the same machine
i have two other dvb cards (TT-S23200)that are working ok. 
I was attracted to TBS because they claim to support Linux and Mythtv...
Is there anyone that can help ??

---

### Post by kamolt on 2012-01-03
Problem solved.
There are 3 dvb cards in this server and Linux allocates the cards not always to same frontend adapter i.e. /dev/dvb/adapterx/frontend0. This means that Mythtv can look at the wrong dvb card. The solution is to force card order of the frontend. Obviously this problem cannot occur if there is only one dvb card installed.
So The TBS6928 card is working quite well now and so is the CI adapter. Here in Belgium I use an Astoncrypt DVB-CI module which works ok with the TBS6928.
I did not see any glitches in SD or HD recordings.

---

