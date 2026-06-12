---
title: "resolv.conf problem for a noob!!!"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by bogart_2003 on 2009-03-15
ok so i have ubuntu 8.04 in a dual boot with windows (used Wubi install) and i'm having a problem connecting to the internet. i use a wired adsl modem. when using windows, the internet connection works fine, but when i switch to ubuntu, i can't seem to get it working after following the basic instructions. 

i found i was stuck when i ran ```
sudo pppoeconf
``` and what i got was:

```
"Sorry, I scanned 2 interface, but the Access concentrator of your provide did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem"

```

i created a thread a few days ago ([http://ubuntuforums.org/showthread.php?t=1093230&page=3](http://ubuntuforums.org/showthread.php?t=1093230&page=3)). a good fellow replied and guided me through this problem. after running a couple of commands, the last one being ```
sudo /etc/init.d/networking restart
```, i got this:

```
* Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.eth0.pid with pid 5647
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:22:15:c5:3b:27
Sending on LPF/eth0/00:22:15:c5:3b:27
Sending on Socket/fallback
grep: /etc/resolv.conf: No such file or directory
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:22:15:c5:3b:27
Sending on LPF/eth0/00:22:15:c5:3b:27
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
[ OK ]

```

he said that the problem lies with resolv.conf. the old thread is gathering dust, and since the problem is getting more specific (i think) i decided to make a new one. i'm not ready to give up on this yet. any response will be highly appreciated.

---

### Post by chili555 on 2009-03-15
I suggest simply creating one.```
sudo gedit /etc/resolv.conf
```If you don't have gedit, you can substitute kate or any other text editor. Then add this:```
#
#test
#
```Save, close and re-run:```
sudo /etc/init.d/networking restart
```

---

### Post by bogart_2003 on 2009-03-16
hey chili555, thanks for replying!

so i did what you told me to do, and after running
```
sudo /etc/init.d/networking restart
```
here's what i got:

```
* Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.eth0.pid with pid 5639 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/eth0/00:22:15:c5:3b:27 
Sending on   LPF/eth0/00:22:15:c5:3b:27 
Sending on   Socket/fallback 
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/eth0/00:22:15:c5:3b:27 
Sending on   LPF/eth0/00:22:15:c5:3b:27 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
                                                                         [ OK ] 
```

what do you suggest i do next? thanks in advance.

---

### Post by chili555 on 2009-03-16
Your network retstart looks normal now; normal for a setup that is not getting an IP address! In your case, I'd believe it's because you have not set up PPPoE properly yet. I'd try:```
sudo pppoeconf
```I have never done this part myself. I actually have a DSL modem that requires PPPoE, however, all the details, user name and password, can be set up directly in the configuration page of the modem.

---

### Post by bogart_2003 on 2009-03-16
i ran:
```
 sudo pppoeconf
```
and it said:
```
 I found 2 ethernet devices:    
eth0                                                 
eth0:avahi 

Are all your ethernet interfaces listed above? 
(If No, modconf will be started so you can load the
card drivers manually).

Or press ESC to abort here.
```

so i selected "Yes" and after some "loading bars", here's what i got:
```
 Sorry, I scanned 2 interfaces, but the Access
 Concentrator of your provider did not respond. Please
 check your network and modem cables. Another reason
 for the scan failure may also be another running pppoe
 process which controls the modem.
```

i tried to set it up directly in the configuration page of the modem, but still i'm having no success.

---

### Post by chili555 on 2009-03-16
Again, *pppoeconf* is beyond my knowledge zone. I believe that either the modem has to be set up for PPPoE, that is, to give the user name, password and maybe a few other details to the DSL provider; or the modem is set up as a pass-through device and the connected computer must provide those details. In my own case, the DSL provider set up the modem to provide the authentication and we hooked a computer to the modem and, with no special configuration, it connected.

I assume you have confirmed that the modem is up and has an outside IP address, that is, it sees the DSL provider's network and the DSL provider's network sees it.

Beyond that, I guess I'd suggest starting a new thread here. You no longer have a resolv.conf issue, you have a pppoeconf issue.

---

