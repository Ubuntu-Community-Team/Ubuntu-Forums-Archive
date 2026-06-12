---
title: "Bluetooth not working on Inspiron 1525"
date: 2011-12-01
forum: Networking &amp; Wireless
---

### Post by Daithi123 on 2011-12-01
Hey everyone, I'm trying to get my bluetooth up and running on my Dell Inspiron 1525 running Natty Narwharl. 

I did a bit of searching and found out I needed the libsmbios-bin package installed, so I installed but to no avail. 

When I type sudo dellWirelessCtl --sw_bt 1 --bt 1 into the terminal I get the following response 

Traceback (most recent call last):
  File "/usr/sbin/dellWirelessCtl", line 36, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.7/locale.py", line 531, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

What does this mean?:confused:

---

