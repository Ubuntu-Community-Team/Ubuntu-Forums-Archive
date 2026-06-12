---
title: "Change wireless card from N to G"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by Koga73 on 2009-10-21
Hey, so I have my wireless card working (D-Link DWA-556), which is a draft N card. I want to use G, not N. I read that you can use something like:
iwconfig wlan0 modu 11g

To change it, but I am unable to get it to work. It says it is unsupported. So I try:
iwconfig wlan0 modulation

And it says it is unable to retrieve available wireless modes. Any suggestions on how I can get it to use G?

---

### Post by coffeeaddict22 on 2009-10-21
Hi,
Sorry if I'm being obvious, but did you try the commands with sudo in front of them?

---

### Post by Koga73 on 2009-10-21
```

root@aj-1:~# sudo iwconfig wlan0 modu 11g
Error for wireless request "Set Modulation" (8B2F) :
    SET failed on device wlan0 ; Operation not supported.
root@aj-1:~# 

```

---

### Post by tad1073 on 2009-10-21
are you wanting to receive or send n or g? If you want to receive g you need to change that in your router.

---

### Post by Koga73 on 2009-10-21
Send. I'm currently receiving g.

---

