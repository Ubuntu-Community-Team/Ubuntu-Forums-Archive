---
title: "USB Modem Tethered to a Palm Centro Missing Destination Error"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by bigal480 on 2009-02-13
I'm a newbie to ubuntu running 8.04 LTS.  I'm attempting to tether a palm centro using USB Modem software.  I followed the instructions and the thread "palm centro as a USB modem" and each time I try to copy files I get this missing destination error:


sudo cp ~/Desktop/drivers/linux/ppp-script-evdo-templates/etc/ppp/peers/ppp-script-treo
cp: missing destination file operand after `/home/hockeyguy20/Desktop/drivers/linux/ppp-script-evdo-templates/etc/ppp/peers/ppp-script-treo'
Try `cp --help' for more information.


I did search these forms and didn't find any resolution.  Can someone steering me in the right direction???

---

### Post by snatches on 2009-06-16
You need a space b/w the 2 file locations, like this:

sudo cp ~/Desktop/drivers/linux/ppp-script-evdo-templates /etc/ppp/peers/ppp-script-treo

---

