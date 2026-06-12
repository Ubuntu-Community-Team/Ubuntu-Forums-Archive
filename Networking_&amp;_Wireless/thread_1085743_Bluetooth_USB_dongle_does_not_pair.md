---
title: "Bluetooth USB dongle does not pair"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by k@e on 2009-03-03
Today, I received a LogiLink Bluetooth USB dongle for my Intrepid desktop, which is reported to work with Linux. Furthermore, I own a netbook (Ideapad S10e, also Intrepid) and a mobile phone (SE K810i), both of which are capable of using bluetooth. I have already successfully established a connection between netbook and mobile phone and now I want to transfer files between it and my desktop using the dongle.

The device is installed properly, lsusb lists the new hardware correctly. Shortly after I plugged in the dongle for the first time, the bluetooth symbol appeared in the panel. No further fiddling or installing drivers was necessary.

Also, the device seems to work as it should. Using the bluetooth-wizard, it finds the other devices, whose bluetooth ability is turned on and their is visibility I have set to "always visible". Now, when I try to connect to either my mobile phone or netbook, it says "Connecting to..." for a while and then "Pairing failed". I know that at this part, a window asking for a pin code is supposed to show up but it doesn't.

I have also tested the dongle with a Windows XP machine. Had to install drivers but no problems here.

I suspect that this is due to a major change between Gutsy and Hardy, where devices that previously showed up using fdisk -l did not show up anymore after upgrading. So I started bluetooth-wizard with super user right - not expecting anything - and was surprised to see that it worked. However, I did not enter the code on my phone and now I am not able to reproduce it again.

What would I have to do to get it working? Any help is highly appreciated.

---

