---
title: "Xbox360 and Ushare help"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by RichardC400 on 2011-03-14
Here's the deal, i want to play my videos on my xbox off of my pc [ubuntu10.10]
I have Ushare configured as follows:

USHARE_NAME=tom-ubuntu
 USHARE_IFACE=xbox *(i created a new wired connection in the network manager (ipV4 set to shared to other computers and that's what i named it)*
 USHARE_PORT=49200 (not sure if that's correct or how i'd go about finding the port)

 USHARE_TELNET_PORT=
 USHARE_DIR=/home/slayton/Videos/
 USHARE_OVERRIDE_ICONV_ERR=
 ENABLE_WEB=yes
ENABLE_TELNET=no

ENABLE_XBOX=yes
ENABLE_DLNA=no

on my xbox i go to test pc connection. it connects to the network but not the pc and goes to PC Not Listed.


help needed

---

### Post by steaksauce on 2011-03-15
> **RichardC400 said:**
> Here's the deal, i want to play my videos on my xbox off of my pc [ubuntu10.10]
USHARE_TELNET_PORT=
 USHARE_DIR=/home/slayton/Videos/
 USHARE_OVERRIDE_ICONV_ERR=
 ENABLE_WEB=yes
ENABLE_TELNET=no

ENABLE_XBOX=yes
ENABLE_DLNA=no


default telnet port is 992

These links may help:
[http://ushare.geexbox.org/#Usage](http://ushare.geexbox.org/#Usage)
[http://ubuntuforums.org/showthread.php?t=632428](http://ubuntuforums.org/showthread.php?t=632428) (dug it up)

Hope this helps

---

