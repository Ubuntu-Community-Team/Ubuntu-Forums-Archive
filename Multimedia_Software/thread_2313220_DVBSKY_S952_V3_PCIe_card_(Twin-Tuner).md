---
title: "DVBSKY S952 V3 PCIe card (Twin-Tuner)"
date: 2016-02-10
forum: Multimedia Software
---

### Post by vs-ruthless on 2016-02-10
Hi Guys,

I'm after some assistance with installing this card on UB14.04. 

Please note I've been using linux for few years now but still consider myself a noob, so go easy on me ;)

I've followed the instruction on [http://www.dvbsky.net/Support_linux.html](http://www.dvbsky.net/Support_linux.html) and am still having issues at it won't scan for channels. Then when I go back into Mythtv card settings again it has an error and cannot see the card :(


Current outout for the following commands.

```
ls /dev/dvb/
adapter0  adapter1
```

```
dmesg | grep -i dvb
[    2.146914] SMI PCIe driver 0000:04:00.0: card detected: DVBSky S952 V3
[    2.255734] DVB: registering new adapter (SMI_DVB)
[    2.561260] SMI PCIe driver 0000:04:00.0: DVB: registering adapter 0 frontend 0 (Montage M88RS6000)...
[    2.569190] SMI PCIe driver 0000:04:00.0: DVBSky SMI PCIe MAC= 00:18:42:54:55:52
[    2.569614] DVB: registering new adapter (SMI_DVB)
[    2.815112] SMI PCIe driver 0000:04:00.0: DVB: registering adapter 1 frontend 0 (Montage M88RS6000)...
[    2.821889] SMI PCIe driver 0000:04:00.0: DVBSky SMI PCIe MAC= 00:18:32:54:55:53
[    7.854258] i2c i2c-2: m88ds3103: downloading firmware from file 'dvb-demod-m88rs6000.fw'
```

Any help would be much appreciated as I'm starting to losing my patients with it and I refuse to go back to windows (apologies for using the "W" word).

---

