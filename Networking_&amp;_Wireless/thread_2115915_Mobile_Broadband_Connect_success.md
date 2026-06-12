---
title: "Mobile Broadband Connect success"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by peterlauri on 2013-02-14
I have a Fujitsu U772 where everything is working, even the Mobile Broadband Modem is recogniced, and when I connect the sim card, create new connection, put proper SIM pin, and try to connect I get "Modem network, Disconnected". This is what shows up in /var/log/syslog, any idea what it can be? 

The only thing in the settings that I cannot manage to setup is the "Modem Initiation Command", can I set that somewhere?

```
Feb 14 17:11:38 pjotr-fujitsu modem-manager[1328]: <info>  (ttyUSB2) opening serial port...
Feb 14 17:11:38 pjotr-fujitsu modem-manager[1328]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Feb 14 17:11:44 pjotr-fujitsu modem-manager[1328]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> disabled)
Feb 14 17:11:44 pjotr-fujitsu modem-manager[1328]: <info>  (ttyUSB2) closing serial port...
Feb 14 17:11:44 pjotr-fujitsu modem-manager[1328]: <info>  (ttyUSB2) serial port closed
Feb 14 17:11:44 pjotr-fujitsu NetworkManager[1376]: <warn> failed to enable/disable modem: (32) Serial command timed out
Feb 14 17:11:50 pjotr-fujitsu NetworkManager[1376]: <info> Activation (ttyUSB2) starting connection 'Sonera 3G'
Feb 14 17:11:50 pjotr-fujitsu NetworkManager[1376]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 14 17:11:50 pjotr-fujitsu NetworkManager[1376]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Feb 14 17:11:50 pjotr-fujitsu NetworkManager[1376]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Feb 14 17:11:50 pjotr-fujitsu NetworkManager[1376]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Feb 14 17:11:50 pjotr-fujitsu modem-manager[1328]: <info>  (ttyUSB2) opening serial port...
Feb 14 17:11:50 pjotr-fujitsu modem-manager[1328]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Feb 14 17:11:56 pjotr-fujitsu modem-manager[1328]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> disabled)
Feb 14 17:11:56 pjotr-fujitsu modem-manager[1328]: <info>  (ttyUSB2) closing serial port...
Feb 14 17:11:56 pjotr-fujitsu modem-manager[1328]: <info>  (ttyUSB2) serial port closed
Feb 14 17:11:56 pjotr-fujitsu NetworkManager[1376]: <warn> GSM modem enable failed: (32) Serial command timed out
Feb 14 17:11:56 pjotr-fujitsu NetworkManager[1376]: <info> (ttyUSB2): device state change: prepare -> failed (reason 'modem-init-failed') [40 120 28]
Feb 14 17:11:56 pjotr-fujitsu NetworkManager[1376]: <warn> Activation (ttyUSB2) failed.
Feb 14 17:11:56 pjotr-fujitsu NetworkManager[1376]: <info> (ttyUSB2): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 14 17:11:56 pjotr-fujitsu NetworkManager[1376]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
Feb 14 17:11:56 pjotr-fujitsu NetworkManager[1376]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Feb 14 17:11:56 pjotr-fujitsu NetworkManager[1376]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Feb 14 17:11:56 pjotr-fujitsu NetworkManager[1376]: <info> Policy set '0024A50F375E' (wlan0) as default for IPv4 routing and DNS.
Feb 14 17:11:56 pjotr-fujitsu NetworkManager[1376]: <info> Policy set '0024A50F375E' (wlan0) as default for IPv4 routing and DNS.

```

---

### Post by nhorvath on 2013-05-03
I had a similar issue then I did what was in this post:
[http://ubuntuforums.org/showthread.php?t=2117747&p=12570431#post12570431](http://ubuntuforums.org/showthread.php?t=2117747&p=12570431#post12570431)

For my tmobile zte 4g usb modem i put the following in pppconfig:
                                             &#9474;              Number   *99#                 Telephone number                  &#9474;                                              
                                             &#9474;              User     username                 ISP user name                     &#9474;                                              
                                             &#9474;              Password password             ISP password                      &#9474;                                              
                                             &#9474;              Speed    115200               Port speed                        &#9474;                                              
                                             &#9474;              Com      /dev/ttyUSB1         Modem com port                    &#9474;                                              
                                             &#9474;              Method   PAP                  Authentication method             &#9474;                                              
                                             &#9474;               

I litterally put username and password as user/pass.
I kept the default name of "provider"
then i ran "pon" and the modem light indicated I connected and I got an ip address for ppp0
I still couldn't connect to the internet though.
I ran "poff" and the modem lights indicated it disconnected.
Then I tried connecting with network manager by selecting my broadband conneciton and it succeeded.

It's a bit of a workaround but at least it works. Hope this helps!

---

