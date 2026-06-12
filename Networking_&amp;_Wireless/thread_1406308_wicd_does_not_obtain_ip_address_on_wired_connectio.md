---
title: "wicd does not obtain ip address on wired connection"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by desertfox13 on 2010-02-13
Running kubuntu karmic, kernel 2.6.31-19, on Asus EEE PC 1000.

WICD 1.7.0. hangs on "wired connection: obtaining ip address...". I have downgraded to 1.6.2 and 1.5.9, but this did not solve the issue.

WICD does work under other circumstances, e.g. wireless connection. (But at home I don't have wireless, but just the modem and ethernet.)

Same wired connection ethernet connection works flawlessly on laptop running Windows XP SP2.

Any help is greatly appreciated.

---

### Post by desertfox13 on 2010-02-14
I have figured out how to fix the problem, which was a simple fix: restart the modem with ethernet cable connected to the laptop. However, WICD now is connected to ETH0 (ethernet connection), but for some reason I cannot connect to the internet. I get the error message "server not found" as if the internet connection was down. But it is not: I can connect to the internet with my windows xp laptop.

Suggestions are appreciated.

Thanks.

---

