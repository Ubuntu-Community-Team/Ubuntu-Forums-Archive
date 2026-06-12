---
title: "Network manager thinks wireless is managed iff it's... disabled"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by mgol on 2010-01-16
When I have wireless turned on (using a switch on the right of my Dell Latitude E6500 case), Network Manager applet (nm-applet) shows that "device is not managed" - the option to enable wireless is greyed-out.

If turn off wifi using this button... NM claims that now I can enable handling wireless device! It's all the opposite to what should be.

Sometimes after I switch off wireless, some networks show in NM for a short time - it seems that they are searched when wifi is turned on using the button, but they are not shown back then. Once I disable wifi, the program must remember those networks and only after a while looses them (when it discovers wifi devices have been turned off).

Due to this bug I am unable to use network at my University campus. Any guesses how could I fix this?

Unfortunately, the proper bug report:
[https://bugs.launchpad.net/bugs/473215](https://bugs.launchpad.net/bugs/473215)
didn't bring much attention and is still of an "undecided" importance... And to me this kind of bug is simply blocking, I have to use Windows at a campus.

---

### Post by Iowan on 2010-01-17
Does */etc/network/interfaces* have more than the two lines defining "lo"?

---

### Post by mgol on 2010-01-17
> **Iowan said:**
> Does */etc/network/interfaces* have more than the two lines defining "lo"?
Nope. This is the first what I checked.

EDIT: it was enough to blacklist dell-laptop module:
```
sudo rmmod dell-laptop
```
I also added it to a blacklist so that it doesn't start by itself. Problem solved.

---

