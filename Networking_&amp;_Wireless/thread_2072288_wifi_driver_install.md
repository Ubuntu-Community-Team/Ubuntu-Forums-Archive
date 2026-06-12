---
title: "wifi driver install"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by rogersaavedra on 2012-10-17
Hello.
I am a new user of Ubuntu.  I just installed Ubuntu 12.04 on a Dell Latitude D430.  I am having issues with my wireless, seems like the driver for the card is missing, found out that it is the BCM5752.  I downloaded and unzipped in a different machine and placed it n the desktop of the machine I installed Ubuntu 12.04.

What is the command to install that driver that is sitting on the desktop?
I will appreciate any other useful commands or a site where I can find them.

Thanks

---

### Post by nativehound on 2012-10-17
I think the bcm5752 is an ethernet card driver.

Try this to find your wifi card model.

```
sudo lshw -C
```

---

### Post by chili555 on 2012-10-17
@nativehound--> sudo lshw -CPlease try this before you post it.

@rogersaavedra--
I'd rather see:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by rogersaavedra on 2012-10-18
This is what I get:

0c:00.0 Network Controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

Do I need to find a driver for this?  so I can have wireless activated? Will appreciate your help.

Thanks.

---

### Post by GreenTaurus on 2012-10-18
[The fix]("http://ubuntuforums.org/showpost.php?p=10527475&postcount=5")

---

### Post by GreenTaurus on 2012-10-18
[The fix]("http://ubuntuforums.org/showpost.php?p=10527475&postcount=5")

---

