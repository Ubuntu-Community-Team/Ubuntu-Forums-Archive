---
title: "Three monitors, Two video cards, Only 1 Works Correctly"
date: 2010-01-05
forum: Multimedia Software
---

### Post by kaspien on 2010-01-05
I have three monitors. Two plugged into an ATI card and the third into an nVidia card.

**Issue #1:** One of the monitors plugged into the ATI card has the wrong resolution, System>Display gives no option to change it to the correct (much bigger) resolution.

**Issue #2:** The monitor plugged into the second video card does not work at all. System>Display does not even show it.

If I run xglrxinfo I get the following:

> stanley: fglrxinfo
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Value in failed request:  0x1
  Serial number of failed request:  18
  Current serial number in output stream:  18
The cards I'm using are both several years old but fully capable of carrying the monitors at the appropriate resolutions:
 - nVidia 6800 GT
 - ATI x1800

When I tried to install the manufacturer's drivers, both ATI and nVidia complained that no corresponding card could be found.

What can I do to resolve this?

---

