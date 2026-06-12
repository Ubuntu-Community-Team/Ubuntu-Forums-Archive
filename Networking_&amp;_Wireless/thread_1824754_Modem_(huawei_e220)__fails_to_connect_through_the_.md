---
title: "Modem (huawei e220)  fails to connect through the network manager"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by cong06 on 2011-08-14
Several times I was having problems with the huawei e220 modem with the network manager. (in ubuntu 11.04)
I would plug it in, then I would connect as soon as it showed up.

However the "enable mobile-broadband" was never auto-checking itself, and the connection was always failing (I noticed that if it didn't auto-check itself, it would fail, even if I enabled it myself through the network manager).

Eventually I found that I needed to follow these steps before each startup after a computer suspend or computer start:
1) If the modem was plugged in when the computer was started, 'modem-manager' had to be reset:
```
sudo pkill modem-manager
```
2) Plug the modem in. Wait about a minute or two.
3) once you're sure that it's stable, (you can check to see when the '/var/log/syslog' output stops) connect through the network manager.

Sometimes I have to do this a few times. After each time I pull out the modem I reset the modem-manager.
Eventually it works.

---

