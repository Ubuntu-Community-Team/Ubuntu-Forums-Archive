---
title: "Can't use USB dial-up modem in Ubuntu"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by hst19 on 2010-02-19
Hi folks!

I need some help installing my modem in ubuntu. Can somebody please help me out?
I'm using an external Huawei CDMA fixed wireless terminal (phone + dial-up modem). It connects to my PC via a USB port. Actually my PC recognizes it (after driver installation) as "TIUMP Serial Port". I guess the driver is a kind of USB adapter for a serial port.

I can't get it to work in ubuntu 9.10. I ran wvdial (after installing dependencies and wvdial package) and it doesn't recognize my device as a modem. 
Is there any solution to this problem? Without solving it, I won't be able to go online from ubuntu. Any tips will be appreciated.

By the way, I'm having booting problems with Karmic, so I'm about to install Hardy instead. If my device has to be configured in different ways in Karmic and Hardy, instructions for both OS's will be helpful.

Thanks!

---

### Post by hst19 on 2010-02-19
> **hst19 said:**
> Hi folks!

I need some help installing my modem in ubuntu. Can somebody please help me out?
I'm using an external Huawei CDMA fixed wireless terminal (phone + dial-up modem). It connects to my PC via a USB port. Actually my PC recognizes it (after driver installation) as "TIUMP Serial Port". I guess the driver is a kind of USB adapter for a serial port.

I can't get it to work in ubuntu 9.10. I ran wvdial (after installing dependencies and wvdial package) and it doesn't recognize my device as a modem. 
Is there any solution to this problem? Without solving it, I won't be able to go online from ubuntu. Any tips will be appreciated.

By the way, I'm having booting problems with Karmic, so I'm about to install Hardy instead. If my device has to be configured in different ways in Karmic and Hardy, instructions for both OS's will be helpful.

Thanks!

Finally, I managed to do it! After tweaking settings in wvdial.cfg file, the modem worked! Still having trouble configuring gnomeppp, but that's a permissions problems and probably can be solved quickly.
In case some one else is having the same problem and browsing these forums for a solution, here's a guide that helped me:

[http://sanjibmukherjee.info/2010/01/reliance-netconnect-ubuntu-910]("http://sanjibmukherjee.info/2010/01/reliance-netconnect-ubuntu-910")

---

