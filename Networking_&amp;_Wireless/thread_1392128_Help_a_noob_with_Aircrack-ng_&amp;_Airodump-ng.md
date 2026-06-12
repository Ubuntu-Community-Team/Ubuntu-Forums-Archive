---
title: "Help a noob with Aircrack-ng &amp; Airodump-ng?"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by SchizmWolf on 2010-01-27
Hey. I'm trying to follow this tutorial on WEP testing/cracking (for educational purposes):  > [http://www.governmentsecurity.org/forum/index.php?showtopic=15149](http://www.governmentsecurity.org/forum/index.php?showtopic=15149)I've gotten kismet working just fine, but the aircrack version specified in the tutorial isn't the same as what I've got, which is aircrack-ng 1.0. It runs fine, but when I try a semingly valid input for the "airodump-ng <wifi interface> <output filename> [mac filter]" it gives me the help screen. I'm extremely new to all this, so any help would be appreciated. Thanks!

---

### Post by sp0nge on 2010-01-27
I believe airodump-ng requires the following:

```
airodump-ng {interface} -w {outputfilename} --channel {#}
```

*Without the {}

---

### Post by SchizmWolf on 2010-01-27
> **sp0nge said:**
> I believe airodump-ng requires the following:

```
airodump-ng {interface} -w {outputfilename} --channel {#}
```*Without the {}

So, just to make this clear, it would be something akin to:
```
airodump-ng wlan0 -w output --channel 11
```
That seem like a valid input?

---

### Post by sp0nge on 2010-01-27
affirmative.

---

