---
title: "3G Connects and Disconnects - Ubuntu 9.10"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by famelboy on 2009-12-30
Hey there!
how are you?

I'm having some problems conecting my Huawei E220 with Vodafone P..
I use wvdial:

fabio@mylaptop:~$ wvdial hsdpa

--> WvDial: Internet dialer version 1.60

--> Cannot get information for serial port.

--> Initializing modem.

--> Sending: ATZ
ATZ
OK

--> Sending: ATZ
ATZ
OK

--> Sending: ATE0v1&D2&C1S0=0+IFC=2,2
ATE0v1&D2&C1S0=0+IFC=2,2
OK

--> Sending: AT+CGDCONT=1,"IP","internet.vodafone.pt";
OK

--> Modem initialized.

--> Sending: ATDT*99***1#

--> Waiting for carrier.
CONNECT

--> Carrier detected.  Starting PPP immediately.

--> Starting pppd at Wed Dec 30 23:35:17 2009

--> Pid of pppd: 2551
--> Using interface ppp0

--> local  IP address 77.54.138.134

--> remote IP address 10.64.64.64

--> primary   DNS address 212.18.160.133

--> secondary DNS address 212.18.160.134

--> Connect time 0.2 minutes.

--> Disconnecting at Wed Dec 30 23:35:29 2009

--> The PPP daemon has died: A modem hung up the phone (exit code = 16)

--> man pppd explains pppd error codes in more detail.

--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

--> Auto Reconnect will be attempted in 5 seconds

--> Cannot open /dev/ttyUSB0: No such file or directory

--> Cannot open /dev/ttyUSB0: No such file or directory

--> Cannot open /dev/ttyUSB0: No such file or directory

--> Disconnecting at Wed Dec 30 23:35:30 2009


i had no problems with ubuntu 7.10 and 8.04
but now the conection is available only 1 or 2 seconds
can someone help please?



Regards

---

### Post by GeorgeVita on 2010-01-01
Hi **famelboy**, happy new year!

**At first check/update your Ubuntu 9.10** with alternative internet connection (if not yet) to remove some bugs initially existed on 3g:```
uname -a
```will show you the kernel version, you need **>= 2.6.31-15-generic**

Some other users report that E220 need firmware update (?), as this is a more difficult update >>> search/learn and then try if you find enough info.

Note also that E220 considered as 'standard' and must work with no 'tricks' via network manager!

Regards,
George

---

### Post by uidb4056 on 2010-01-04
Hi famelboy and GeorgeVita, I have the same USB modem that worked flawlessly with previous releases but didn't work with Karmic x64 on my Lenovo W500 (kernel 2.6.31.16-generic). Found in Launchpad that this can be solved updating the firmware of modem this link will show you the way and includes a link on Launchpad with explanations ( [http://azizan.aiskosong.net/?p=458](http://azizan.aiskosong.net/?p=458) ).

I've switched to XP where the modem runs without problems, downloaded the firmware and applied it (only the firmware not the dashboard because Launchpad says is not necessary), after the update of firmware in XP I've checked if still runs on it and Yes! it still works and get as a side benefit that the connection now is at 7.2 GB instead of previous 3.6 GB.

Going back to Karmic again now at connection of the USB the internal disk is showed in desktop but , when starts the modem it was started OK but I was not able to navigate ...

Searching for a solution (apparently the problem was no DNS) I edited the wideband connection starting from terminal 'sudo nm-connection-editor' and in the Tab 'Adjusting IPV4' fill the field DNS Servers with the DNS used by XP and then this was solved.

I hope this can help

---

### Post by famelboy on 2010-01-05
Hey!
I'm now connected to the world on my Ubuntu :D
I've updated my Huawei E220 firmware
and the network manager did it's job now :)

My kernel: 2.6.31-16-generic
Connected with Vodafone Portugal

Thanks
F.Rosa

---

