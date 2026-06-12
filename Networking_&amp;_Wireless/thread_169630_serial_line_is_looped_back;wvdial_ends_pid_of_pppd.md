---
title: "serial line is looped back;wvdial ends pid of pppd#"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by rolypolycat on 2006-05-03
Hello!
I have  Hayes Accura 5674US, 56k+fax external modem, ttyS1 on a Compaq Presario 4400. I'm using Breezy.  I've used both pppconfig and wvdialconfig.  When I dial up using pon or sudo wvdial, here are the results of both logs:
************

wvdial log 5/03/06

michelle@mainframe:~$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT822-5473
--> Waiting for carrier.
ATDT822-5473
CONNECT 115200
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed May  3 00:10:11 2006
--> pid of pppd: 13970

ppp dialup log
michelle@mainframe:~$ sudo tail -f /var/log/syslog
May  3 00:12:18 localhost chat[14649]: abort on (NO DIALTONE)
May  3 00:12:18 localhost chat[14649]: abort on (NO DIAL TONE)
May  3 00:12:18 localhost chat[14649]: send (ATZ^M)
May  3 00:12:18 localhost chat[14649]: expect (OK)
May  3 00:12:19 localhost chat[14649]: ATZ^M^M
May  3 00:12:19 localhost chat[14649]: OK
May  3 00:12:19 localhost chat[14649]:  -- got it
May  3 00:12:19 localhost chat[14649]: send (ATDT8225473^M)
May  3 00:12:19 localhost chat[14649]: expect (CONNECT)
May  3 00:12:19 localhost chat[14649]: ^M
May  3 00:12:43 localhost chat[14649]: ATDT8225473^M^M
May  3 00:12:43 localhost chat[14649]: CONNECT
May  3 00:12:43 localhost chat[14649]:  -- got it
May  3 00:12:43 localhost chat[14649]: send (^M)
May  3 00:12:43 localhost pppd[14648]: Serial connection established.
May  3 00:12:43 localhost pppd[14648]: Using interface ppp0
May  3 00:12:43 localhost pppd[14648]: Connect: ppp0 <--> /dev/ttyS1
May  3 00:13:08 localhost pppd[14648]: Serial line is looped back.
May  3 00:13:08 localhost pppd[14648]: Connection terminated.
*******************
May  3 00:13:39 localhost chat[15116]: send (ATZ^M)
May  3 00:13:39 localhost chat[15116]: expect (OK)
May  3 00:13:39 localhost chat[15116]: ATZ^M^M
May  3 00:13:39 localhost chat[15116]: OK
May  3 00:13:39 localhost chat[15116]:  -- got it
May  3 00:13:39 localhost chat[15116]: send (ATDT8225473^M)
May  3 00:13:39 localhost chat[15116]: expect (CONNECT)
May  3 00:13:39 localhost chat[15116]: ^M
May  3 00:14:04 localhost chat[15116]: ATDT8225473^M^M
May  3 00:14:04 localhost chat[15116]: CONNECT
May  3 00:14:04 localhost chat[15116]:  -- got it
May  3 00:14:04 localhost chat[15116]: send (^M)
May  3 00:14:04 localhost pppd[14648]: Serial connection established.
May  3 00:14:04 localhost pppd[14648]: Using interface ppp0
May  3 00:14:04 localhost pppd[14648]: Connect: ppp0 <--> /dev/ttyS1
May  3 00:14:35 localhost pppd[14648]: LCP: timeout sending Config-Requests
May  3 00:14:35 localhost pppd[14648]: Connection terminated.
May  3 00:14:36 localhost chat[15427]: abort on (BUSY)
May  3 00:14:36 localhost chat[15427]: abort on (VOICE)
May  3 00:14:36 localhost chat[15427]: abort on (NO CARRIER)
May  3 00:14:36 localhost chat[15427]: abort on (NO DIALTONE)
May  3 00:14:36 localhost chat[15427]: abort on (NO DIAL TONE)
May  3 00:14:36 localhost chat[15427]: send (ATZ^M)
May  3 00:14:36 localhost chat[15427]: expect (OK)
May  3 00:14:43 localhost chat[15427]: ^M
May  3 00:14:43 localhost chat[15427]: NO CARRIER
May  3 00:14:43 localhost chat[15427]:  -- failed
May  3 00:14:43 localhost chat[15427]: Failed (NO CARRIER)
May  3 00:14:43 localhost pppd[14648]: Connect script failed
May  3 00:14:44 localhost pppd[14648]: Modem hangup

Wvdial asssigns a pid to the process, but I can't go anywhere in firefox; in fact, I'm not sure I'm connected. PON either times out or gives me the "serial line is looped back" garbage. Using the GUI gnome ppp in Networking does nothing at all. What is the problem here, and how do I fix it in one or the other? Until I get online, I can't upgrade or add any needed software except doing things the long way around through WinXP. Any help is appreciated!

Sincerely,

Michelle

---

