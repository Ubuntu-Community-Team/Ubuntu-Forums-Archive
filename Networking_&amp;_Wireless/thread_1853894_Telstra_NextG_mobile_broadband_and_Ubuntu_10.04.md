---
title: "Telstra NextG mobile broadband and Ubuntu 10.04"
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by BigBaka on 2011-10-03
I'm visiting my mum in Australia from overseas where I live, and she has recently started using Telstra mobile broadband using a Sierra Wireless USB mobile broadband adapter. I'm only visiting for two weeks but wanted to be able to plug it into my Ubuntu 10.04, but telstra is typically useless in providing anything but Windows and Mac support, and have no idea how to set anything up apart from running the install file located on the device.

I tried to use the network connections in Ubuntu and add the mobile broadband device, but it did not seem to work, and I wasn't sure of the problem or trouble shooting options.

Any tips on getting this mobile broadband adapter to run on 10.04 without screwing up the mobile broadband adapter too much so that my mum won't run into problems using it on her windows machine after I've gone?

Regards,
BB

---

### Post by BigBaka on 2011-10-21
Good news, 

I managed to get the Mobile Broadband going. The trick was to find out which model of modem I was using and then just search on google for a solution. In doing so I found this which put me in the right direction.
[http://kyliebraindump.blogspot.com/2011/02/telstra-sierra-wireless-312u-aircard.html](http://kyliebraindump.blogspot.com/2011/02/telstra-sierra-wireless-312u-aircard.html)

I needed to install two programs from the software center, Gnome PPP and wvdial. I used Gnome PPP to detect the modem port and then I needed to edit the wvdial.conf file which was a hidden file in the home directory, and then inserted the following [modem port as per Gnome PPP].

```
[Dialer Defaults]
Modem = /dev/ttyUSB2
Init = AT+CGDCONT=1,"IP","telstra.bigpond"
Phone = *99#
Username = enterusername@bigpond.com
Password = enterpassword
New PPPD = yes
Stupid Mode = on
```

After restarting, I could go through the standard ubuntu mobile broadband setup process to open the connection.

Regards,
BB

---

