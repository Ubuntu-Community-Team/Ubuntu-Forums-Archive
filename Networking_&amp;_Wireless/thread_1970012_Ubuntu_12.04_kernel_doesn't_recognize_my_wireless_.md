---
title: "Ubuntu 12.04 kernel doesn't recognize my wireless card"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by mikerobinson on 2012-04-30
Upon upgrading to Ubuntu 12.04 my wireless card is no longer recognized by the OS. I installed Wicd in hopes that I would be able to connect with that, but it is a no-go this time. eth1 (my wireless device) doesn't even show up as an interface. When I boot to the 3.0.0 kernel I am able to connect like normal, but when using 3.2 it doesn't work. How can I debug this?

---

### Post by chili555 on 2012-04-30
Just a guess, but what kind of Broadcom is it? Please open a terminal and run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by mikerobinson on 2012-04-30
```
06:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
```

---

### Post by chili555 on 2012-04-30
Your card is claimed by no less than *three* competing drivers. We may have to work out which is best. With a wired ethernet connection, please do:```
sudo su
apt-get install --reinstall bcmwl-kernel-source
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

---

### Post by kchangj on 2012-05-02
I have a similar problem except I get:


06:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

Do I still follow the same steps from before?

---

### Post by chili555 on 2012-05-02
> Do I still follow the same steps from before?Not quite. I've had a problem with people reading and following instructions for a different card and complaining that it didn't work. Your card is different. Please start a new thread and give your details above. I'll be right there to help you.

---

