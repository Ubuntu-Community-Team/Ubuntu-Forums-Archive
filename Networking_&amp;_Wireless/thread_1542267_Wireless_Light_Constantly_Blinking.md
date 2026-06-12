---
title: "Wireless Light Constantly Blinking"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by RaynerJ on 2010-07-30
Hey guys,

I am new to Ubuntu and am confused on how to fix my flashing wireless light issue.  After browsing Google people are recommending that I make a script and put it into a folder, but when I try to put the file in there I get an error of "Error moving file: Permission denied".

Code in script:

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
  for dir in /sys/class/leds/iwl-phy*; do
    echo none > $dir/trigger
  done
fi

Location: network - if-up.d

If you need anymore information, please ask.

James

---

### Post by Iowan on 2010-07-30
The "Error moving" message sounds like you may need to use **sudo**.

---

