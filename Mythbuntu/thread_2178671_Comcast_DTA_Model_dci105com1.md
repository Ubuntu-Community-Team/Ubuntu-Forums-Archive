---
title: "Comcast DTA Model dci105com1"
date: 2013-10-04
forum: Mythbuntu
---

### Post by betolley on 2013-10-04
My DTA and hardware works in Windows but I hate it.  I can't get LIRC to work with any conf files that I find.  Does anyone have experence using the comcast dci105com1 dta?  I purchased a newer blaster because I thought it was a problem with it but I still can't get it to work.  I tried making my own conf using irrecord.  Only button that worked with 5.  But it did work in LIRC so the hardware works.  Basically I can send the signal with irsend and the light blinks(i see with my camera).  But nothing will work with any external config and button 5 works for me with my config.  I have my config listed below.

Mythbuntu 12.04 32bit

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.9.0(default) on Fri Oct  4 12:38:38 2013
#
# contributed by
#
# brand:                       lircd.conf
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name  lircd.conf
  flags RAW_CODES
  eps            30
  aeps          100

  gap          81445

      begin raw_codes

          name BTN_0
              200     950     150    1700     250     750
              200    2800     250    1250     250    1250
              250    1150     250    2650     200   12950
              200     950     150    2800     250     750
              200     750     200     800     200     750
              200     750     200     750     200

          name BTN_1
              250     850     250    1650     250     800
              150    2800     250    1250     250    1300
              200    1150     250    2650     250   12900
              250     900     150    2650     250     800
              200     750     200     750     200     850
              250     750     200     800     150

          name BTN_2
              250     850     250    1700     200     750
              200    2800     250    1300     200    1300
              250    1100     250    2650     250   12900
              250     850     250    2500     250     700
              250     700     250     750     200    1000
              250     750     200     750     200

          name BTN_3
              300     800     300    1600     300     650
              300    2750     300    1200     300    1250
              250    1100     300    2600     300   12850
              300     800     250    2350     300     650
              300     650     300     700     250    1100
              300     650     300     650     300

          name BTN_4
              300     800     300    1650     250     700
              300    2700     300    1250     250    1250
              300    1050     300    2600     300   12850
              300     800     300    2150     300     700
              250     700     300     650     300    1200
              300     700     250     700     300

          name BTN_5
              250     900     200    1650     250     800
              150    2800     250    1250     250    1300
              200    1150     250    2650     250   12900
              200     950     150    2100     250     800
              150     800     200     750     200    1400
              250     750     200     800     150

          name BTN_6
              250     900     200    1650     250     750
              200    2800     250    1250     250    1300
              200    1150     250    2650     250   12900
              250     900     200    1950     250     700
              250     700     250     750     200    1550
              250     750     200     750     200

          name BTN_7
              250     900     200    1700     200     750
              200    2800     250    1300     200    1300
              250    1100     250    2650     250   12900
              250     900     200    1800     250     800
              150     750     200     800     200    1650
              250     800     150     800     200

          name BTN_8
              250     850     250    1650     300     650
              300    2750     300    1200     300    1200
              300    1100     300    2600     250   12900
              250     800     300    1650     300     650
              300     650     300     700     250    1800
              300     650     300     650     300

          name BTN_9
              250     900     200    1700     200     750
              200    2800     250    1300     200    1300
              250    1100     250    2650     250   12900
              250     900     200    1550     200     750
              250     750     200     700     250    1950
              250     750     200     750     250

      end raw_codes

end remote
```

---

