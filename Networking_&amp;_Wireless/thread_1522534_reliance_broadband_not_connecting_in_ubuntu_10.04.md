---
title: "reliance broadband not connecting in ubuntu 10.04"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by tanixmukherzee on 2010-07-02
i earlier used bsnl broadband(indian) in ubuntu and configure it using pppoeconf. right now i shifted to reliance broadband(not usb modem) but now pppoeconf cannot detect the connection
It shows something like " Sorry I scanned two interfaces but the access concentrator of ur provider did not respond.plz chck ur ntwrk and modem cables. anoder reason fir the scan failure may be anoder running pppoe process which controls the modem

---

### Post by Iowan on 2010-07-02
From Code of Conduct:
> Please use color and font properties for highlighting portions of your text, and not for all of the text in your post. 

:D

---

### Post by dineshs on 2010-07-02
I hope you have a DSL modem connected via ethernet.Am I right?
> " Sorry I scanned two interfaces but the access concentrator of ur provider did not respond.plz chck ur ntwrk and modem cables. anoder reason fir the scan failure may be anoder running pppoe process which controls the modem 
If the broadband modem is configured in PPPoE mode(also called `always on' mode where the username and password are stored in the modem)you need not configure the connection using the DSL tab in NM or try pppoeconf command.You can directly use web browser.If you try pppoeconf in this case you may get such an error.Please ping an open DNS such as 4.2.2.1 and post the result
```
ping 4.2.2.1 -c3
```
pl also post the output of
```
ifconfig -a
```

---

