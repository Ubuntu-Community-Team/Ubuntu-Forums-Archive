---
title: "can't find wlan0"
date: 2011-11-18
forum: Networking &amp; Wireless
---

### Post by ccb147 on 2011-11-18
Hi All,

I'm new to the forums and fairly new to ubuntu.  When I first installed 11.04 everything magically worked wirelessly.  Upon upgrading to 11.10, I couldn't find wlan0 using iwconfig so I reverted to 11.04 and found wlan0 but it said the essid was "off".  After what I hoped would be some tweaks to turn it "on", I messed things up to the point where it was just easier to re-install 11.04.  Now that I have done that, I can't find wlan0 again.  When I run iwconfig eth0 and lo tell me "no wireless extensions" but no wlan0.  Also, ifconfig only lists eth0 and lo as well.

Please help!!

---

### Post by ccb147 on 2011-11-18
also, and this is probably redundant, there is no option to "enable wireless networking" under the quick-link drop down menu in the upper-right corner.

---

### Post by ccb147 on 2011-11-19
to the top

---

### Post by wojox on 2011-11-19
What wireless are you using:
```
lspci | grep -i net
```

---

### Post by ccb147 on 2011-11-19
I believe ispci, however I'm not entirely sure (not sure how to check).

---

