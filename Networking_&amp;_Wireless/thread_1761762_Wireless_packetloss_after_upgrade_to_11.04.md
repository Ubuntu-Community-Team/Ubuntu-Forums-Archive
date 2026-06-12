---
title: "Wireless packetloss after upgrade to 11.04"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by DustWolf on 2011-05-18
Hello,

I have a MSI U100 netbook with a Ralink RT2860 wireless module. On 10.04 it worked fine in my apartment but after an upgrade to 11.04 I am seeing a 7% packet loss and on occasion a line less on my wireless receptivity. I cannot explain in any other way than that it is caused by the upgrade.

I am noting these in the syslog that were not there before:
> May 18 00:21:32 dustball kernel: [   12.379593] cfg80211: World regulatory domain updated:
May 18 00:21:32 dustball kernel: [   12.379604] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 18 00:21:32 dustball kernel: [   12.379615] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 18 00:21:32 dustball kernel: [   12.379625] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 18 00:21:32 dustball kernel: [   12.379635] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 18 00:21:32 dustball kernel: [   12.379644] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 18 00:21:32 dustball kernel: [   12.379654] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

Followed by a repeating pattern of these for different frequencies:
> May 18 00:21:32 dustball kernel: [   12.416375] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
May 18 00:21:32 dustball kernel: [   12.416389] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)

Could this have something to do with my problems? If yes, how do I kill it? :)

EDIT: I live in the EU and use a Netgear accesspoint that never worked well with laptops brought in the USA. :P

LP,
Jure

---

### Post by DustWolf on 2011-05-18
I found this:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/365049]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/365049")

...now to find out where that "lw" command is hiding...

---

### Post by DustWolf on 2011-05-18
And hopefully the solution ($ prefix means you type what follows in a terminal):
[LIST=1]
[*] $ sudo apt-get install iw
[*] $ sudo gedit /etc/init.d/setwirelesscountrycode.sh
[*] put in:
```
#!/bin/bash
##iw reg set <your-country-code>
iw reg set CC
```
...where CC is [your Country Code by ISO 3166-1 alpha-2]("http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2"). For me this is "SI" without quotes.
[*] $ sudo chmod +x /etc/init.d/setwirelesscountrycode.sh
[*] $ sudo update-rc.d setwirelesscountrycode.sh defaults
[*] reboot
[/LIST]

I actually tried typing all of this.

CREDIT: [http://ubuntuforums.org/archive/index.php/t-1324288.html]("http://ubuntuforums.org/archive/index.php/t-1324288.html")

LP,
Jure

---

### Post by DustWolf on 2011-05-18
Meh it's not helping T.T

Screw the law and give me back my wireless!

---

### Post by jawilljr on 2011-05-18
I'll bet that it is Network-Manager's "background scanning" to find out install WICD and purge network-manager the reboot.

If that works then you can either keep WICD or install [this patch](http://nilvec.com/disable-scanning-in-networkmanager-when-connected/) to network-manager.

```
sudo apt-get install wicd
sudo apt-get purge network-manager
sudo reboot
```

Jerry

---

### Post by DustWolf on 2011-05-19
New info: No packetloss when the charger is connected.

When running on battery, the following thing changes when the error occurs, when running "$ iwconfig wlan0":
> Tx excessive retries:12  Invalid misc:3

Both figures are zero when wifi works fine.

I guess this is a driver issue.

---

### Post by DustWolf on 2011-05-19
Seems related: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594866](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594866)

EDIT: Blacklisted the rt2800pci driver and suddenly my reception is a whole lot better! Everything back to normal now, problem solved.

---

