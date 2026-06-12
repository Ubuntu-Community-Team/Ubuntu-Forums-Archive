---
title: "upgraded to 8.10 lost wireless on a thinkpad x40"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by jesusfanclub on 2008-12-02
please help,

Mark.

---

### Post by mikeh on 2009-03-28
Stick to 8.04 - works perfectly with the X40.
too many problems in 8.10

---

### Post by iponeverything on 2009-03-28
Go to:

System -> Preferences -> Sessions 

Click "+ Add" and fill in the fields as follows:

Name:      Network Manager
Command:   nm-applet --sm-disable
Comment:   Network Manager applet

Then restart..

---

### Post by superprash2003 on 2009-03-28
in your terminal , type the following commands and post output
1)lshw -C network
2)iwconfig
3)iwlist scanning

---

