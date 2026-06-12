---
title: "Custom Mobile Broadband Connection"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by louigi600 on 2009-09-15
I need to setup a custom mobile broadband connection in order to specify APN server as opposed to the provider defaults.
I've used the "Network Connections" to create a new mobile broadband connection end then edited it to customize APN, username, password, and authentication method.
This is what is logged:
```
Sep 17 09:50:09 eng-prova pppd[11902]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin
.so loaded.
Sep 17 09:50:09 eng-prova pppd[11902]: pppd 2.4.5 started by root, uid 0
Sep 17 09:50:09 eng-prova pppd[11902]: Using interface ppp0
Sep 17 09:50:09 eng-prova pppd[11902]: Connect: ppp0 <--> /dev/ttyUSB0
Sep 17 09:50:12 eng-prova pppd[11902]: PAP authentication succeeded
Sep 17 09:50:14 eng-prova pppd[11902]: Modem hangup
Sep 17 09:50:14 eng-prova pppd[11902]: Connection terminated.
Sep 17 09:50:15 eng-prova pppd[11902]: Exit.

```

And that is not me terminating  connection


Can anyone help me get this right ?
I'm running Ubuntu 9.0.4 Desktop AMD64 on a Fujitsu Esprimo Mobile and a TIM branded E620 usb broadband stick with a TIM sim.

---

### Post by louigi600 on 2009-09-15
BTW: manually configuring the connection (the old command line way) works fine and connects.

---

### Post by louigi600 on 2009-09-17
This is how the manual setup was done:

/etc/ppp/peers/eng
```
/dev/ttyUSB0
noipdefault
defaultroute
persist
nodetach
usepeerdns
name _<mu username ... pap-secrets consistently populated>_
debug
connect "/usr/sbin/chat -vf /etc/ppp/chatscripts/eng.chat"
```/etc/ppp/chatscripts/eng.chat
```
TIMEOUT 3
ABORT BUSY
ABORT 'NO CARRIER'
ABORT VOICE
ABORT 'NO DIALTONE'
ABORT 'NO DIAL TONE'
ABORT 'NO ANSWER'
ABORT DELAYED
"" ATZ
OK-ATZ-OK ATX3Q0V1E1S0=0&C1&D2
OK-AT-OK AT+CGDCONT=1,"IP","<will not show this>"
OK ATDT*99#
CONNECT ""
```And magically "pppd call eng" produces this log:
```
Sep 17 09:54:52 eng-prova pppd[11937]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Sep 17 09:54:52 eng-prova pppd[11937]: pppd 2.4.5 started by root, uid 0
Sep 17 09:54:52 eng-prova pppd[11937]: Using interface ppp0
Sep 17 09:54:52 eng-prova pppd[11937]: Connect: ppp0 <--> /dev/ttyUSB0
Sep 17 09:54:55 eng-prova pppd[11937]: PAP authentication succeeded
Sep 17 09:54:57 eng-prova pppd[11937]: Modem hangup
Sep 17 09:54:57 eng-prova pppd[11937]: Connection terminated.
Sep 17 09:54:58 eng-prova pppd[11937]: Exit.
Sep 17 10:10:08 eng-prova pppd[12913]: pppd 2.4.5 started by eng, uid 0
Sep 17 10:10:09 eng-prova chat[12915]: timeout set to 3 seconds
Sep 17 10:10:09 eng-prova chat[12915]: abort on (BUSY)
Sep 17 10:10:09 eng-prova chat[12915]: abort on (NO CARRIER)
Sep 17 10:10:09 eng-prova chat[12915]: abort on (VOICE)
Sep 17 10:10:09 eng-prova chat[12915]: abort on (NO DIALTONE)
Sep 17 10:10:09 eng-prova chat[12915]: abort on (NO DIAL TONE)
Sep 17 10:10:09 eng-prova chat[12915]: abort on (NO ANSWER)
Sep 17 10:10:09 eng-prova chat[12915]: abort on (DELAYED)
Sep 17 10:10:09 eng-prova chat[12915]: send (ATZ^M)
Sep 17 10:10:09 eng-prova chat[12915]: expect (OK)
Sep 17 10:10:09 eng-prova chat[12915]: ^M
Sep 17 10:10:09 eng-prova chat[12915]: OK
Sep 17 10:10:09 eng-prova chat[12915]:  -- got it 
Sep 17 10:10:09 eng-prova chat[12915]: send (ATX3Q0V1E1S0=0&C1&D2^M)
Sep 17 10:10:09 eng-prova chat[12915]: expect (OK)
Sep 17 10:10:09 eng-prova chat[12915]: ^M
Sep 17 10:10:09 eng-prova chat[12915]: ATX3Q0V1E1S0=0&C1&D2^M^M
Sep 17 10:10:09 eng-prova chat[12915]: OK
Sep 17 10:10:09 eng-prova chat[12915]:  -- got it 
Sep 17 10:10:09 eng-prova chat[12915]: send (AT+CGDCONT=1,"IP","<will not show this>"^M)
Sep 17 10:10:09 eng-prova chat[12915]: expect (OK)
Sep 17 10:10:09 eng-prova chat[12915]: ^M
Sep 17 10:10:09 eng-prova chat[12915]: AT+CGDCONT=1,"IP","<will not show this>"^M^M
Sep 17 10:10:09 eng-prova chat[12915]: OK
Sep 17 10:10:09 eng-prova chat[12915]:  -- got it 
Sep 17 10:10:09 eng-prova chat[12915]: send (ATDT*99#^M)
Sep 17 10:10:09 eng-prova chat[12915]: expect (CONNECT)
Sep 17 10:10:09 eng-prova chat[12915]: ^M
Sep 17 10:10:09 eng-prova pppd[12913]: Serial connection established.
Sep 17 10:10:09 eng-prova pppd[12913]: Using interface ppp0
Sep 17 10:10:09 eng-prova pppd[12913]: Connect: ppp0 <--> /dev/ttyUSB0
Sep 17 10:10:10 eng-prova pppd[12913]: PAP authentication succeeded
Sep 17 10:10:15 eng-prova pppd[12913]: Could not determine remote IP address: defaulting to 10.64.64.64
Sep 17 10:10:15 eng-prova pppd[12913]: local  IP address <will not show this>
Sep 17 10:10:15 eng-prova pppd[12913]: remote IP address <will not show this>
Sep 17 10:10:15 eng-prova pppd[12913]: primary   DNS address <will not show this>01
Sep 17 10:10:15 eng-prova pppd[12913]: secondary DNS address <will not show this>
Sep 17 10:10:38 eng-prova pppd[12913]: Terminating on signal 2
Sep 17 10:10:38 eng-prova pppd[12913]: Connect time 0.4 minutes.
Sep 17 10:10:38 eng-prova pppd[12913]: Sent 0 bytes, received 0 bytes.
Sep 17 10:10:38 eng-prova pppd[12913]: Connection terminated.
Sep 17 10:10:39 eng-prova pppd[12913]: Exit.
```This time it was me that terminated the connection.

How do I get this working correctly with the Network Manager ?

---

### Post by louigi600 on 2009-09-17
bounce !

---

