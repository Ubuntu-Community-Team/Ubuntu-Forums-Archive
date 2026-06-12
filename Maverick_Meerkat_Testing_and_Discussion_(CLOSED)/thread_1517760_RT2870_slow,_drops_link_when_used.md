---
title: "RT2870 slow, drops link when used"
date: 2010-06-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rbmorse on 2010-06-25
My test machine uses a Linksys WUSB600n USB wireless interface (RT2870). Maverick detects the device and successfully negotiates a WPA2 connection.  However, the link is reported as a 12Mbps connection and if I try and actually do anything with it, like use a browser or update the machine, the connection drops and cannot be reestablished.  

Anyone else seeing similar behavior?  Any ideas for a fix or work-around?

---

### Post by autocrosser on 2010-06-26
Did you try this? >>>>  [http://ubuntuforums.org/showthread.php?t=1342593&highlight=RT2870](http://ubuntuforums.org/showthread.php?t=1342593&highlight=RT2870)

I would guess that info is still good for Maverick.....

---

### Post by rbmorse on 2010-06-26
It is.  Thanks.  Blacklisting the community drivers did the trick.

---

### Post by Talon2 on 2010-06-27
It is good to talk about things like this but if we don't file bugs or add to existing bug reports, the information may not get to the correct place.

Here is a bug that appears to be the same as what you are reporting:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

This is not a new issue.  Pile on this bug.

---

