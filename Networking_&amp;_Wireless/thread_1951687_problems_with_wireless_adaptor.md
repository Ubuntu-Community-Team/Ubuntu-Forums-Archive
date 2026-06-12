---
title: "problems with wireless adaptor"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by ziacko93 on 2012-04-02
hey, i am having a ****-tonne of trouble with my netgear wireless adaptor(WNA3100), i have downloaded all the adjacent drivers possible, i have installed windows wireless drivers and when i type ip addr, i get information for my eth0, lo, and wwan(i think its supposed to be wlan0, which is the source of my problems i believe).

Basically, when i install the drivers using windows wireless drivers and try to configure them, nothing really haddens in that when i try to add a new wireless connection, all the options are greyed out.  i have looked up a tonne of guides, none of which solve my propblem.

---

### Post by UltimateCat on 2012-04-03
Check that you have the right drivers.

You are right it is suppose to be
 ```
wlan0

```
Mine was set to etho and it wouldn't work but I also had to include the "inf" file in the process of installing along with the Windows Wireless Drivers. 

You can find the inf file on the cd that came with the adapter.

Sometimes firmware can aid a driver but not always. You could research this as I am not 100% sure-

[http://www.netgear.com/home/products/wireless-adapters/](http://www.netgear.com/home/products/wireless-adapters/)

[http://support.netgear.com/app/answers/detail/a_id/17393/~/wna3100-software-version-1.1.3.22](http://support.netgear.com/app/answers/detail/a_id/17393/~/wna3100-software-version-1.1.3.22)
[http://forum1.netgear.com/showthread.php?t=55364](http://forum1.netgear.com/showthread.php?t=55364)
Solved
[http://www.fixya.com/tags/wna3100_driver](http://www.fixya.com/tags/wna3100_driver)

---

