---
title: "Modem switching problem in USB 3G Modem."
date: 2013-08-03
forum: Networking &amp; Wireless
---

### Post by Ashfaqur Rahman on 2013-08-03
Problem:
I have a USB 3G modem. Which is ZTE MF190. When I plug this modem ```
lsusb
``` gives vendor ID: **19d2** and product ID: **0154**. And in this case I get no internet access. But when I plug and unplug modem for 3 to 4 times product ID changed to **2003** and then I get internet access. Sometimes I have to plug and unplug modem for 5 to 6 times or even restart. Yes! if I boot my PC with modem plugged it gets product ID **2003** automatically. Now how can I solve this problem so that when I plug the modem and product ID change automatically without unplugging again.

What I Have Done Already:
I have tried to understand this manual [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/). Actually didn't understand fully.
I have usb_modeswitch in my PC version 1.2.3.
I have found a configuration package in /usr/share/usb_modeswitch and in that configuration i have found a text file( [http://paste.ubuntu.com/5944932/](http://paste.ubuntu.com/5944932/) ) named 19d2:0154. In that file target product ID is set to 0117 I have changed It to 2003. But it didn't work. I enabled log for usb_modeswitch. When modem switch successfully( after plugging and unplugging 3 or 4 times ) it gives this log - [http://paste.ubuntu.com/5944950/](http://paste.ubuntu.com/5944950/) . But when fails(most of the times) it gives this log - [http://paste.ubuntu.com/5944953/](http://paste.ubuntu.com/5944953/).
I have also tried ```
[COLOR=#0000B4][FONT=Courier]usb_modeswitch -v 0x19d2 -p 0x0154 -V 0x19d2 -P 0x2003 -s 20 -M[/FONT][/COLOR]
``` But I can't understand how I can get message counter.

---

