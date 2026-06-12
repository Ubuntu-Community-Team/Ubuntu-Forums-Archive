---
title: "cant bring up the wireless interface back"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by t_virus on 2009-03-26
can you help me in one thing?

when i start airmon-ng i destroy the managed wireless to put it in monitor mode. but then when i'm finished i try to put back the ath0 in managed mode and i cant... gives an error:

mauro@mauro-laptop:~$ airserv-ng -d ath1
Opening card ath1
socket(PF_PACKET) failed: Operation not permitted
This program requires root privileges.
airserv-ng: wi_open(): Illegal seek
mauro@mauro-laptop:~$ sudo airserv-ng -d ath1
Opening card ath1
Setting chan 1
Opening sock port 666
Serving ath1 chan 1 on port 666
Connect from 127.0.0.1
Connect from 127.0.0.1
Death from 127.0.0.1
Death from 127.0.0.1
^C
mauro@mauro-laptop:~$ sudo airmon-ng stop ath1


Interface   Chipset      Driver

wifi0      Atheros      madwifi-ng
ath1      Atheros      madwifi-ng VAP (parent: wifi0) (VAP destroyed)


mauro@mauro-laptop:~$ ifconfig ath0 up
ath0: ERROR while getting interface options: device unexistent
mauro@mauro-laptop:~$

even with sudo this happens...
can you help me with this?
thankx

---

