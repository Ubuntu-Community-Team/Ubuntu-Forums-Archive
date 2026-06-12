---
title: "Cannot connect internet using SE W660i suddenly"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by oyko on 2009-06-02
I got problem , when connecting to the internet with SE W660i. Several days before I can connect this W660i as a modem, but I don't know why this day I can not connect? Please help me???
Thank you

---

### Post by GeorgeVita on 2009-06-02
Hi **oyko**,
I do not know if I can help you as I do not have a W660i, but I am sure that you should give more info about your configuration and type of problem you have:

- what Ubuntu varsion you are using?
- how are you connecting the phone/modem to the PC (USB/Bluetooth)?
- does the system recognizes your phone/modem (now or in the past)?
- have you setup anything in the past (while connected?)
- Country/provider ?

Regards,
George

---

### Post by oyko on 2009-06-03
I use Ubuntu Jaunty 9.04 kernel 2.6.28.12.
I use usb to connect to the PC, the system recognize my phone (now and in the past), and I still can connect to the internet with usb mode, but I cannot connect with mobile broadband which is setup in Ubuntu.
I have setup before in the past, Country Indonesia, provider Telkomsel.
I do not know when I try to connect to internet using mobile broadband is failed.
Thanks

---

### Post by GeorgeVita on 2009-06-03
Hi **oyko**, most times the disconnection (or no connection) via Network Manager is due to "conflicts" with Wireless, Ethernet or some IPv4 settings.
Just an idea is to disable wireless (if any) and disconnect ethernet. Also try to delete all previous connections, reboot and set up via the wizard (as the system recognises your phone).

Regards,
George

P.S. If you still have the problem, please describe the "I still can connect to the internet with usb mode" and post any error or disconnection message trying via Network Manager.

---

