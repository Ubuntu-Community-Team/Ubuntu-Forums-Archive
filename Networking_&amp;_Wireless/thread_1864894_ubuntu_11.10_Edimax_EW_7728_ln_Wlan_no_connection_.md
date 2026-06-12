---
title: "ubuntu 11.10 Edimax EW 7728 ln Wlan no connection HELP PLS"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by quangvinh on 2011-10-19
hello everyone, 
as a student i need ubuntu to learn Opal, the functional programm language.
but i am a pretty new Ubuntuuser, so i want to ask you some questions about WLAN.

i installed the newest ubuntu 11.10 and have an Edimax EW 7728 ln PCI Wlan Card, which have the Ralink RT2860 Chip, i think.
Ubuntu can connect to my Wlan Router, but i still dont have internet connection, i dont know why. Can you pls help me pls. I have read old posts and do some pictures with commandos to get information:

sudo lshw -C network:
[IMG]http://s1.directupload.net/images/111019/4ri22wic.png[/IMG]


[B]
sudo lspci -nnk | grep -iA2 net : [/B]
[IMG]http://s1.directupload.net/images/111019/3mqvqeiu.png[/IMG]


[B]iwconfig:

[IMG]http://s7.directupload.net/images/111019/geuhk78o.png[/IMG]
[/B]


[B]rfkill list all:

[IMG]http://s1.directupload.net/images/111019/86fr7gsa.png[/IMG]
[/B]

[B]lsmod:

[IMG]http://s1.directupload.net/images/111019/8jem32ll.png[/IMG]
[/B]

**sudo cat /var/log/syslog | grep -e wl -e firmware -e wlan0** **| tail n35**
[IMG]http://s14.directupload.net/images/111019/qohdw8e4.png[/IMG]

---

### Post by quangvinh on 2011-10-19
nobody has idea?

---

### Post by pdc on 2011-10-19
thank you for all the detail;

only problem with images is I can't copy and paste data into google to search

if one searches on the ID of your device (1814:0601)

seems like rt2800pci should be the right driver

[http://wiki.debian.org/rt2800pci](http://wiki.debian.org/rt2800pci)

suggest issue command

> modprobe rt2800pci

---

### Post by ProDG_Yodha on 2011-10-19
Hi, 
unsure if this is of any help but,check [FONT="Times New Roman"][SIZE="3"]*ifconfig*[/SIZE][/FONT] output.
If ifconfig shows you with the correct ip, then see if you can [FONT="Times New Roman"][SIZE="3"]*ping google.com*[/SIZE][/FONT]. If there is no IP, then try ```
sudo dhclient wlan0
```

~My first reply :)

---

### Post by chicoff on 2011-10-22
this is the bug report for the Edimax EW-7811Un USB dongle

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190)

maybe this can help you, but there is still no solution

---

