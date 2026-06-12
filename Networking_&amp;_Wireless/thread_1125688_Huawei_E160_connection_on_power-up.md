---
title: "Huawei E160 connection on power-up"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by pteja on 2009-04-14
Hi,

I have been breaking my head for the past several days on a seemingly simple problem. Here it is:

I want to connect my Huawai E160 3G modem to a USB port on a computer running Ubuntu 8.04. I need to keep the modem connected to the computer and go online whenever I switch on the computer which means the modem needs to get connected once the computer powers on.

After 2 days I was able to connect to the Internet using wvdial. Many thanks to all the helpful posts in this forum.

Problem: After powering on the computer, I must disconnect the modem and reconnect it to make it work - else I get this error:

> Cannot open /dev/ttyUSB0: Device or resource busy 

Any ideas to get over this?

I suspect it is related to the mass storage part of the device which is somehow "busy"...

---

### Post by pteja on 2009-04-27
OK! Got this solved. I am not sure what made it work.

I did the following:

1. Replaced the USB modem with a different USB modem - I do not think this made any difference.

2. Inserted the line:
```
SUBSYSTEM=="usb", SYSFS{idProduct}=="<YourDefaultProdID>", SYSFS{idVendor}=="<YourDefaultVendID>", RUN+="<YourPathToUSB_ModeSwitch>"
```

in a new file here:
```
/etc/udev/rules.d/46-hotplug.rules
```

You can find excellent help on this here:
[http://www.draisberghof.de/usb_modeswitch/]("http://www.draisberghof.de/usb_modeswitch/")

3. Downloaded & installed usb_modeswitch (see 2 above).

4. In the wvdial (several posts on this in this forum), added two sections - one for sending the PIN to the modem and the other to actually connect and combined the two in the session startup in a simple .sh file (basically calls both scripts one after another).
 
Useful threads in this forum:
[http://ubuntuforums.org/showthread.php?t=262867]("http://ubuntuforums.org/showthread.php?t=262867")
[http://ubuntuforums.org/showthread.php?t=1128097]("http://ubuntuforums.org/showthread.php?t=1128097")

BTW: 
Tried the Vodafone - worked intermittently
Tried kppp - did not work - I also gave up once I could get connected ;-)

---

