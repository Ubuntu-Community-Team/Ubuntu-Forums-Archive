---
title: "MTP Question"
date: 2014-06-13
forum: Multimedia Software
---

### Post by GrouchyGaijin on 2014-06-13
Hi Guys,

Could someone explain to me why it is that I can connect my mp3 player to lubuntu 14.04 and it will mount, open the device in the file manager and allow me to drag and drop mp3 files into the device yet I can not seem to access the device via the command line?

I should rephrase that.  I can access the device using mtp-tools, but am plagued by the device is busy errors.
mtp-detect gives me this error:
```

Unable to open ~/.mtpz-data for reading, MTPZ disabled.libmtp version: 1.1.6

```
Then goes on to list my device.

Just for grins I made the file ~/.mtpz-data and tried again, thinking maybe it couldn't be opened because it was not there.
The error message changed slightly to:
```
Unable to read MTPZ public exponent from ~/.mtpz-data, MTPZ disabledlibmtp version: 1.1.6 
```

---

### Post by Bucky Ball on 2014-06-13
*Thread moved to **Multimedia & Video**.*

---

### Post by Vladimir_Oufa on 2014-12-30
You should be able to see your files by : ls -l /run/user/$(id -u)/gvfs/mtp*/

---

### Post by GrouchyGaijin on 2014-12-31
Thank you

---

