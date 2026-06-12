---
title: "PPP server and mgetty...."
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by angelogomes on 2009-04-01
I am having a strange and weird behavior with mgetty in Ubuntu 8.04

I followed the tutorial to install a PPP server in this link

[http://ubuntuforums.org/showthread.php?t=150339](http://ubuntuforums.org/showthread.php?t=150339)

My modem is now a Linmodem ;) (HSF Conexant SL2801) and it is working as I could check using wvdialconf and wvdial. The port is ttySHSF0.

I did everything in that guide but the mgetty keeps trying to use a ttyS0 port and so it does not access the modem to initialize it.

I checked the /var/log/mgetty directory and it creates a log file mg_log.ttyS0 file

The weird thing is if I run manually mgetty with the command

"mgetty /dev/ttySHFS01"  it does work and it creates the correct log file mg_log.ttySHF0

Noting that I´ve changed the inittab file, that seems to be not used anymore since ubuntu 6.10 , and also create the files ttySHSF0 and mgetty in the /etc/event.d as reported by other users at the same topic above.



So my question is: why the hell mgetty is not working as configured ? Is it a mgetty bug ?



Angelo

---

