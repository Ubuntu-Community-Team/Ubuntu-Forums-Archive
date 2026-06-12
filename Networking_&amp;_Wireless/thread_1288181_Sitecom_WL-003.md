---
title: "Sitecom WL-003"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by F-3000 on 2009-10-11
This USB-wlan device works with Ubuntu (9.04) when doing this trick:

1. Get drivers from [http://atmelwlandriver.sourceforge.net/downloads.html](http://atmelwlandriver.sourceforge.net/downloads.html) (I didn't need to do the mentioned kernel patch).

2. Unpack, then open terminal, and *cd* to the unpacked folder/directory.

3. Type (or copy/paste) these lines: 
```
sudo make usb buildonly=debug

sudo make install

sudo depmod -aeq
```

4. Reboot.


**FYI**
This wlan device (or driver) supports only (few types of) WEP and LEAP encrypting.

---

