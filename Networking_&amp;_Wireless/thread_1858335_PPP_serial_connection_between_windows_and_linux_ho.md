---
title: "PPP serial connection between windows and linux hosts"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by lilorox on 2011-10-12
Hi,

I'm trying to directly connect two hosts (one Windows XP, the other Ubuntu 11.04) with a serial cable.
I think I got the Windows side configured (as a client) but I have no clue as how to configure the Ubuntu host.

I understand that everything is happening in the /etc/pppd/options.ttyS0 file (there is only one serial pot on the machine so I guess it's /dev/ttyS0) but I cannot find anything useful about this configuration.

I'd like to attribute an IP to each hosts and make them communicate directly because they are on different LAN and the network is not very reliable. As a consequence, synergy is disconnecting regularly.

Can anyone help with this?

Thanks in advance,
LiLo

---

### Post by alexfish on 2011-10-12
this is a link from an old thread
 
[http://howto.gumph.org/content/xp-direct-cable-to-linux/](http://howto.gumph.org/content/xp-direct-cable-to-linux/)
 
[http://ubuntuforums.org/showthread.php?t=1027535](http://ubuntuforums.org/showthread.php?t=1027535)
 
see if it helps , don't forget to configure samba ,
 
alexfish

---

### Post by SeijiSensei on 2011-10-12
Personally I'd just buy two ethernet cards and a crossover cable.

Speaking of crossover cables, you are using a crossover ("null modem") serial cable, right?  Regular serial cables won't work for interconnection.  Crossovers connect the transmit pins on one end to the receive pins on the other, and vice versa.

[PPP HOWTO](http://tldp.org/HOWTO/PPP-HOWTO/)

See especially [chapter 29](http://tldp.org/HOWTO/PPP-HOWTO/direct.html).

---

### Post by lilorox on 2011-10-13
Thanks for the answers!

I know that two ethernet cards and a crossover cable would be easier but the PCs I would like to connect are small desktops from my company and I wouldn't touch the hardware as they are under the responsibility of another company... Plus I don't own any ethernet card that would fit in the half-size slot... :(

I checked that the cable I use is similar to a null-modem cable but I'm not entirely sure of it and I don't have any tool to verify the pin-out...
It's actually a failover cable but I read (on F5 networks website) that the pinout is the same.

---

### Post by lilorox on 2011-10-13
BTW, I am trying SLIP too. It seems a little bit easier than PPP for the configuration.

---

### Post by alexfish on 2011-10-13
for info about cables can have a look here

[http://linuxgazette.net/issue41/smyth.html](http://linuxgazette.net/issue41/smyth.html)  (type used for win 95 and Linux ppp)

[http://www.lammertbies.nl/comm/info/RS-232_null_modem.html](http://www.lammertbies.nl/comm/info/RS-232_null_modem.html)

[http://en.wikipedia.org/wiki/Null_modem](http://en.wikipedia.org/wiki/Null_modem)

when powered up you need to check if the null modem is working , 

 check if serial port is listing  under the root dialout , should show as ttyS0 and possible ttyS1
from web info, ttyS1 is the connection

 ```
ls -al /dev/ttyS*
```or can also check see if a modem is registered[FONT=monospace] , but can't confirm this will show any device , but interesting to find the results

[/FONT]```
dmesg | grep -e "modem" -e "tty"
```
alexfish

---

### Post by lilorox on 2011-10-14
The ttyS0 is working fine, it is present in dmesg and the rights were initially root:dialout but I changed them to uucp:dialout to use cu.

Is there a way to test this cable and know if it is a null-modem?

I thought about open an HyperTerminal on one end and a screen/cu/minicom on the other end but it doesn't seem to work... :(

---

