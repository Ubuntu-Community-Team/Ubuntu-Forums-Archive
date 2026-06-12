---
title: "Help! : can not find the wireless router with Broadcom 4328"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by qinyian on 2009-05-23
Hello:

I'm suing a HP Tx2000 notebook with Broadcom 4328 wireless card. Sometimes I can find my router at the NetworkManager,but sometimes not. I can always connect to the router under Windows, or use my Thinkpad X61 with Intel wireless card. More interesting, "not found" does not mean the Broadcom 4328 does not work at all. It can find my neighborhoods' routers, a lot of.

What's the problem? I'm really confused.

---

### Post by Shadowmeph on 2009-05-23
Not sure if you did this but I had to turn on the hardware driver ( I don't have the exact name right now because I am not on my LAptop which is using Ubuntu but it is listed under system administration hardware

---

### Post by qinyian on 2009-05-23
Yes, I have turn the driver on. I'm suing Ubuntu 9.04 with Broadcom STA wireless driver.

---

### Post by Ayuthia on 2009-05-23
Are you able to see your router from the Terminal:
```
sudo iwlist scan
```

If you are able to see it consistently, then I am thinking that the issue might be with NetworkManager.

Also is the router using WEP/WPA/WPA2?

---

### Post by qinyian on 2009-05-25
I have tried iwlist scan. But I still can't find it. The router is using WAP2 Personal. Why the router is hidden to my Hp laptop, but not for My thinkpad? Is it the problem of the Broadcom driver? I'm using Ubuntu 9.04 64bit and the broadcom STA driver.

---

### Post by Ayuthia on 2009-05-25
I'll have to test it out with my laptop when I have a chance.  I know that the Broadcom STA module sometimes does have problems with encrypted networks but as far as I know, you should still be able to see your router just not be able to connect to it.  The only exception to this might be if you have your router set to have a hidden SSID.

---

