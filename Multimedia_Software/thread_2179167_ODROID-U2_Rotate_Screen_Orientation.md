---
title: "ODROID-U2 Rotate Screen Orientation"
date: 2013-10-06
forum: Multimedia Software
---

### Post by schmidtbag on 2013-10-06
I own the ARM platform called ODROID-U2 with Linaro 12.11 installed on it, kernel 3.0.62.  I have the mali drivers installed and supposedly working (glxgears runs anyway).

However, I can't rotate the screen 90 degrees into portrait mode, I get the following error when running randr -o left:
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14
```


Does anyone have any suggestions on "forcing" the screen to rotate?

---

