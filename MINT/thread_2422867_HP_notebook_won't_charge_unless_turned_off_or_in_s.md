---
title: "HP notebook won't charge unless turned off or in suspended state"
date: 2019-07-14
forum: MINT
---

### Post by nfi2 on 2019-07-14
Hi All,

Long time lurker first time poster. After a few years of using Linux Mint on my notebook I finally talked my wife into using the same on hers after Windows stuffed up. I've always found any problems I've had have already been answered here and now that we don't have a windows machine of course I can't find an answer to my problem. 

My wife is running Linux Mint 19 on her HP notebook model 15-af124au. Everything seems to be working fine except it won't charge unless the lid is closed or it is powered down. It seems to be a problem with HP notebooks in general but the only fixes I can find are .exe related which is not an option anymore.

Response from upower -i /org/freedesktop/UPower/devices/battery_BAT1 below._BAT1
  native-path:          BAT1
  vendor:               111-83-72
  model:                HS04041
  serial:               19838 07/10/2015
  power supply:         yes
  updated:              Sun 14 Jul 2019 15:22:00 AEST (34 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              20.72 Wh
    energy-empty:        0 Wh
    energy-full:         30.9912 Wh
    energy-full-design:  30.9912 Wh
    energy-rate:         10.0788 W
    voltage:             15.622 V
    time to empty:       2.1 hours
    percentage:          66%
    capacity:            100%
    icon-name:          'battery-full-symbolic'
  History (charge):
    1563081720    66.000    discharging
  History (rate):
    1563081720    10.079    discharging

One suggestion I have seen is to unplug, power down and then plug back in and power up to see if it is a suspend problem but this doesn't fix it either.

Just wondering if anyone has any other suggestions?

---

### Post by wildmanne39 on 2019-07-14
Hello and welcome to the forum!

*Thread moved to **MINT a more appropriate sub-forum**.*

---

### Post by nfi2 on 2019-07-15
Anyone have any suggestions?

---

### Post by nfi2 on 2020-01-06
Just wondering if anyone might have any starting points of what to look for? This is really killing me because it is my wife's laptop and I have to hear about it every time she opens it.

---

