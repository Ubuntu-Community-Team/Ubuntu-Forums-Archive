---
title: "Need help connecting to wireless."
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by GreenBowlPacker_3 on 2009-05-02
I'm using Ubuntu 9.04 and it reconizes my wireless card but I can't connect to any wireless network.  Do I need to install something else?  I'm using a Dell Inspiron 1501 with a broadcom wireless card.

---

### Post by Ayuthia on 2009-05-02
Usually with the Broadcom cards, you need to go into System->Administration->Hardware Drivers and activate the Broadcom card option.  Have you tried that yet?  If so, can you post the results of:
```
lspci -nn|grep 14e4
```

---

### Post by GreenBowlPacker_3 on 2009-05-02
That worked, thanks!

---

### Post by digby on 2009-05-02
If I can add a related question:
I'm on an old Dell Latitude D600.  When I go to System -> Admin ->  Hardeware Drivers, I get the message that 'No proprietary drivers are in use on this system.'  I don't have any option to enable anything. 

The output of the aforementioned command is```

~$ lspci -nn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14E4:165D] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
```Thanks

---

