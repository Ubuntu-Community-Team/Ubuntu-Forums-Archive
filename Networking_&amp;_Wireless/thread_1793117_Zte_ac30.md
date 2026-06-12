---
title: "Zte ac30"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by alx96 on 2011-06-29
Hello,

I have a GSM/CDMA modem AC30 from ZTE.
It has a USB connector and can function as Access Point.

It works well in Windows, but I primarily use Ubuntu, and I can not
seem to get it to work on my 10.04.

I tired using the default PPP settings in 10.04, and I also tried
using gnome-PPP. Ubuntu just wont detect the AC30.

Do I need some kind of driver to get it work?
I searched for such driver but I could not find it.

Any ideas?

regards,
Alex

---

### Post by alexfish on 2011-06-30
Hi

may work out of the box in Ubuntu 10.10

[http://markpareja.com/blog/?p=16](http://markpareja.com/blog/?p=16)

if in 10.04 can post results of these commands from the terminal
connect the device give time for the system to settle

```
lsusb
```
```
dmesg | grep -e "modem" -e "tty"
```
```
tail -f /var/log/syslog
```

alexfish

---

