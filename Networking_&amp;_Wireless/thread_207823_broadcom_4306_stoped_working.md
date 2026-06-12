---
title: "broadcom 4306 stoped working"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by DR_K13 on 2006-07-02
i cant connect. I re-installed fwcutter, bcmwl5.sys drivers, mobprobed. and still no dice. in " windows drivers " nothing shows up.  I really need to do to work today so I need some help fixing this!

I will be happy to post outputs


please help!


Thanks

---

### Post by DR_K13 on 2006-07-02
ok following this wiki page,[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
I get this output





sean@lappy:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules

---

### Post by DR_K13 on 2006-07-02
mabe I am almost there.....




I cant connect the card


























ok... now it sees the card, but not the network

---

### Post by DR_K13 on 2006-07-02
ok, I have to $ sudo modprobe bcm43xx
every time I reboot to it can see the card, but it still will not see the network

---

### Post by ubunturules on 2006-07-04
Use ndiswrapper its a lot easier and your connection will be faster.  Here's a HOWTO I wrote.
[http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper+54+mbps](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper+54+mbps)

---

