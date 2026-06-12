---
title: "one solution for karmic wifi problems on Eee PC 1000HE"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by jpn213 on 2009-12-30
I was having random wifi disconnects and they seemed to correlate with high CPU usage.  

I added this script to /etc/network/if-up.d to give the wifi card a large number of retries in the case of dropped or missed packets, and now the connection is solid.  There may be a more elegant solution, but this got things working.

```

#!/bin/bash

# Fix random dropped connections when CPU load is too high
# on Eee PC 1000HE running ath9k driver

/sbin/iwconfig wlan0 retry 255

```

---

### Post by scathmandra on 2010-01-19
Looks good, but I have a beginner's question: once the script is in there, how do I make it execute?

---

