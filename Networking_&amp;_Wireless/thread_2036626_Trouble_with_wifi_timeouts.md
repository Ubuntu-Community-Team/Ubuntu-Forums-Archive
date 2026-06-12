---
title: "Trouble with wifi timeouts"
date: 2012-08-02
forum: Networking &amp; Wireless
---

### Post by beeltejuice on 2012-08-02
Below is the dmesg output -- anybody seen anything like this before?  I'm not sure where to start...

Wifi was working this morning but was sloooowwwww.  I rebooted then could not get it to go again. Tried rebooting the laptop and the router a few times.  Also tried connecting to my phone's wifi hotspot, got same errors.

```

[  354.988849] wlan0: authenticate with 68:7f:74:08:05:81 (try 1)
[  355.064495] wlan0: authenticated
[  355.084564] wlan0: associate with 68:7f:74:08:05:81 (try 1)
[  355.284094] wlan0: associate with 68:7f:74:08:05:81 (try 2)
[  355.483560] wlan0: associate with 68:7f:74:08:05:81 (try 3)
[  355.683062] wlan0: association with 68:7f:74:08:05:81 timed out
...
[  780.954419] wlan0: authenticate with 68:7f:74:08:05:81 (try 1)
[  781.153858] wlan0: authenticate with 68:7f:74:08:05:81 (try 2)
[  781.353395] wlan0: authenticate with 68:7f:74:08:05:81 (try 3)
[  781.552836] wlan0: authentication with 68:7f:74:08:05:81 timed out
...
[  801.219508] wlan0: direct probe to 68:7f:74:08:05:81 (try 1/3)
[  801.418850] wlan0: direct probe to 68:7f:74:08:05:81 (try 2/3)
[  801.618431] wlan0: direct probe to 68:7f:74:08:05:81 (try 3/3)
[  801.817923] wlan0: direct probe to 68:7f:74:08:05:81 timed out

```

---

