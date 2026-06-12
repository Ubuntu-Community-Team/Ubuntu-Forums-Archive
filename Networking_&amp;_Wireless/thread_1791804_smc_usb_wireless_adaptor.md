---
title: "smc usb wireless adaptor"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by hsaptus on 2011-06-27
trying to install RT2870 Chipset Based USB Wireless Adapter using this guide:

```
http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html
```

I'm failing to compile the drive :( 
I just wanted to keep my WPA2 psk encryption. 

Any idea would be great. Thanks in advance,
H

---

### Post by chili555 on 2011-06-27
Depending on your Ubuntu version, rt2870sta is included already so there is usually no need to compile. Let's troubleshoot. Please run and post fro a terminal:```
lsusb
uname -r
```Thanks.

---

### Post by hsaptus on 2011-06-27
oh men.... never mind... its way to stupid from my part. but many thanks for trying to help me. Its very simple... i configured my router 2 years ago and totally forgot i was mac filtering it :D
Of course that adapter wouldn't connect. 

Again, many thanks for the reply never the less. And yes, rt2870sta is included, but after googling for some weird reason (instead of looking at the obvious) i come up with this idea that WPA wasn't active for some reason since every one was having the some issue.

---

