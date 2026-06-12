---
title: "Eeepc 1000H RT2860STA New Drivers"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by kyle6513 on 2010-06-22
Heres the deal, I installed the latest drivers (make & make install) from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) the rt2860sta drivers,
followed a few guides suspecting it was the little discrepencies in the configuration files but to no avail.
ifconfig and iwconfig both report that the adapter (ra0, previously wlan0) is up and running, NetworkManager is running but does not appear in the system tray. rt2860sta is reported in lsmod | grep rt2860sta as rt2760sta 768309 1. I'm at a loss, all I wanted was to keep up to date :-k

can anyone provide me with troubleshooting ideas or some way to revert to the previously installed drivers?

running ubuntu 10.04 LTS (as updated as it was when the wireless failed)
running linux kernel 2.6.32-21-generic. PLEASE HELP ME :confused:

---

### Post by kyle6513 on 2010-06-24
I hate to do this but, bump.

---

### Post by bluefrog on 2010-06-24
have a look there:

[https://bugs.launchpad.net/bugs/496093](https://bugs.launchpad.net/bugs/496093)

---

### Post by kyle6513 on 2010-06-24
thanks blue frog! poked around and found,
[http://ubuntuforums.org/showthread.php?t=1045703](http://ubuntuforums.org/showthread.php?t=1045703)
many thanks, this should suffice (:

---

### Post by kyle6513 on 2010-06-24
annnd im still stuck in the same situation although, the network manager has a wireless networks section now, but has device not managed greyed out, no idea why it's rejecting my card as you can see, it's up and running,
> ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=100/100  Signal level:-66 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

