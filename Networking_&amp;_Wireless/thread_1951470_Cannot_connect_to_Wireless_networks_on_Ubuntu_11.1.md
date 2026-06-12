---
title: "Cannot connect to Wireless networks on Ubuntu 11.10 on Dell Inspiron 1525"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by SunJune on 2012-04-02
Hi,

I know there are countless methods and ways posted on the forums all over the place for wireless connection issues in Ubuntu 11.10, but I couldn't solve it after 2 full days of tinkering. I have installed this as a dual boot with Windows Vista using wubi on 32 bit dell inspiron 1525. 

To make matter worse, I don't have wired internet connection in this locality, only wireless internet, so the only option is to work on this problem without internet.

Can somebody please help. 

Thanks

---

### Post by chili555 on 2012-04-02
Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by SunJune on 2012-04-04
Thanks for the info, but I got it working by using a wireless USB adapter.

I then activated the wireless driver and now it is working fine.

Thanks

---

### Post by chili555 on 2012-04-04
> **SunJune said:**
> Thanks for the info, but I got it working by using a wireless USB adapter.

I then activated the wireless driver and now it is working fine.

ThanksIf you'd ever like to troubleshoot and activate the internal device, please post back; I'll be happy to help.

---

