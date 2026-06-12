---
title: "Problem with Sierra Wirless AC850 under Ubuntu 10.04"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by achim_59 on 2010-12-13
In keeping with my attemps to document my unhappy experiences with this card, I'm starting a new thread to detail my progress. I started a thread some years ago with loads of info which is no longer relevant, since I have made a good deal of progress. Back then I was using Feisty, but I've upgraded afew times since then.

I keep trying every few months (when I get some spare time) and am now at the point where I make a connection but the card simply hangs up. Previously I had an error, which came about because the card doesn't recognise the [i]AT_OPSYS[i] command in the chatscript. I've removed that and now get a connection... then the modem terminates the connection and I have no idea why.

The /etc/ppp/peers script looks like this:

```

-detach
/dev/umts
460800
debug
defaultroute
usepeerdns
user wapuser1
show-password
crtscts
lock
## 
## the eplus version with symlinkk /dev/umts...
##
#/dev/ttyUSB0
#/dev/umts
#460800
#crtscts
#lock
#defaultroute
#mtu 1500
#mru 1500
#debug
#idle 300
idle 30
##
## some other options (including compression protocol stuff)
##
noccp
noauth
noipdefault
novj
nomagic
maxfail 40
persist
##
## Specify user and call chat script
##
#user umts
user eplus
connect '/usr/sbin/chat -v -f /etc/chatscripts/eplus'

```

The options "maxfail 40" and "persist" meant that when I entered *pon*, the chatscript just kept on trying every 30 seconds and then immediately hanging up (occassionaly I get a termination with "NO CARRIER", too). 

Note that I have the card mapped to /dev/umts and that works. Here is the rule in in /lib/rules.d/99-aircard.rules:

```

# Original suggested script
# BUS=="pcmcia", SYSFS{card_id}=="0x0710", NAME="umts", SYMLINK="tts/umts", RUN+="/usr/local/bin/umtsinit" 
# If correct, should add the pin for umts card init
# additioal: NO PIN!! There is no pin script defined. The pin on the aircard has been turned off.
BUS=="pcmcia", SYSFS{card_id}=="0x0710", NAME="umts", SYMLINK="tts/umts", RUN+="/usr/local/bin/umtsinit"

```

There is no "umtsinit" script, but that doesn't seem to matter, since I get a connection anyway.

I can "talk" to the card using the command *screen /dev/umts*. This allows me to enter AT-commands manually. That's how I discovered that my earlier error was due to the AT_OPSYS command. Leaving that out allowed me to get a connection.

Here's the chatscript:

> 
TIMEOUT 240
ABORT "NO CARRIER"
ABORT "NO DIALTONE"
ABORT "ERROR"
ABORT "NO ANSWER"
ABORT "BUSY"
#"" "+++atz"
"" "ATZ"
OK "ATE0V1"
#OK "AT_OPSYS=3,2"
#OK "AT_OPSYS=1,2"
OK AT+CGDCONT=1,"IP","internet.eplus.de","",0,0
OK "ATD*99***1#"
"CONNECT" ""


Finally, here's the result as logged in /var/log/syslog:

> 
Dec  6 09:36:50 achim-laptop kernel: [ 3684.811409] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
Dec  6 09:36:50 achim-laptop kernel: [ 3684.855576] pcmcia 0.0: firmware: requesting cis/SW_8xx_SER.cis
Dec  6 09:36:51 achim-laptop kernel: [ 3684.951498] 0.0: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
Dec  6 09:36:51 achim-laptop modem-manager: (ttyS2) opening serial device...
Dec  6 09:37:42 achim-laptop pppd[1781]: pppd 2.4.5 started by achim, uid 1000
Dec  6 09:37:43 achim-laptop chat[1784]: timeout set to 240 seconds
Dec  6 09:37:43 achim-laptop chat[1784]: abort on (NO CARRIER)
Dec  6 09:37:43 achim-laptop chat[1784]: abort on (NO DIALTONE)
Dec  6 09:37:43 achim-laptop chat[1784]: abort on (ERROR)
Dec  6 09:37:43 achim-laptop chat[1784]: abort on (NO ANSWER)
Dec  6 09:37:43 achim-laptop chat[1784]: abort on (BUSY)
Dec  6 09:37:43 achim-laptop chat[1784]: send (ATZ^M)
Dec  6 09:37:43 achim-laptop chat[1784]: expect (OK)
Dec  6 09:37:43 achim-laptop chat[1784]: ATZ^M^M
Dec  6 09:37:43 achim-laptop chat[1784]: OK
Dec  6 09:37:43 achim-laptop chat[1784]:  -- got it
Dec  6 09:37:43 achim-laptop chat[1784]: send (ATE0V1^M)
Dec  6 09:37:43 achim-laptop chat[1784]: expect (OK)
Dec  6 09:37:43 achim-laptop chat[1784]: ^M
Dec  6 09:37:43 achim-laptop chat[1784]: ATE0V1^M^M
Dec  6 09:37:43 achim-laptop chat[1784]: OK
Dec  6 09:37:43 achim-laptop chat[1784]:  -- got it
Dec  6 09:37:43 achim-laptop chat[1784]: send (AT+CGDCONT=1,"IP","internet.eplus.de","",0,0^M)
Dec  6 09:37:44 achim-laptop chat[1784]: expect (OK)
Dec  6 09:37:44 achim-laptop chat[1784]: ^M
Dec  6 09:37:44 achim-laptop chat[1784]: ^M
Dec  6 09:37:44 achim-laptop chat[1784]: OK
Dec  6 09:37:44 achim-laptop chat[1784]:  -- got it
Dec  6 09:37:44 achim-laptop chat[1784]: send (ATD*99***1#^M)
Dec  6 09:37:44 achim-laptop chat[1784]: expect (CONNECT)
Dec  6 09:37:44 achim-laptop chat[1784]: ^M
Dec  6 09:37:44 achim-laptop chat[1784]: ^M
Dec  6 09:37:44 achim-laptop chat[1784]: CONNECT
Dec  6 09:37:44 achim-laptop chat[1784]:  -- got it
Dec  6 09:37:44 achim-laptop chat[1784]: send (^M)
Dec  6 09:37:44 achim-laptop pppd[1781]: Script /usr/sbin/chat -v -f /etc/chatscripts/eplus finished (pid 1783), status = 0x0
Dec  6 09:37:44 achim-laptop pppd[1781]: Serial connection established.
Dec  6 09:37:44 achim-laptop pppd[1781]: using channel 1
Dec  6 09:37:44 achim-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec  6 09:37:44 achim-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec  6 09:37:44 achim-laptop pppd[1781]: Using interface ppp0
Dec  6 09:37:44 achim-laptop pppd[1781]: Connect: ppp0 <--> /dev/umts
Dec  6 09:37:45 achim-laptop pppd[1781]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
Dec  6 09:37:45 achim-laptop pppd[1781]: rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0x80c15e7> <pcomp> <accomp>]
Dec  6 09:37:45 achim-laptop pppd[1781]: sent [LCP ConfRej id=0x0 <magic 0x80c15e7>]
Dec  6 09:37:45 achim-laptop pppd[1781]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
Dec  6 09:37:45 achim-laptop pppd[1781]: sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MD5> <pcomp> <accomp>]
Dec  6 09:37:45 achim-laptop pppd[1781]: sent [LCP EchoReq id=0x0 magic=0x0]
Dec  6 09:37:45 achim-laptop pppd[1781]: rcvd [LCP DiscReq id=0x2 magic=0x80c15e7]
Dec  6 09:37:45 achim-laptop pppd[1781]: rcvd [CHAP Challenge id=0x1 <38bb91953ea69a92a27b18e7343f5df8>, name = "UMTS_CHAP_SRVR"]
Dec  6 09:37:45 achim-laptop pppd[1781]: sent [CHAP Response id=0x1 <3aa4b4b049746c240989c7e22d2ee039>, name = "eplus"]
Dec  6 09:37:45 achim-laptop pppd[1781]: rcvd [LCP EchoRep id=0x0 magic=0x80c15e7 00 00 00 00]
Dec  6 09:37:45 achim-laptop pppd[1781]: rcvd [CHAP Success id=0x1 ""]
Dec  6 09:37:45 achim-laptop pppd[1781]: CHAP authentication succeeded
Dec  6 09:37:45 achim-laptop pppd[1781]: CHAP authentication succeeded
Dec  6 09:37:45 achim-laptop kernel: [ 3739.495902] PPP Deflate Compression module registered
Dec  6 09:37:45 achim-laptop pppd[1781]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15>]
Dec  6 09:37:45 achim-laptop pppd[1781]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Dec  6 09:37:45 achim-laptop pppd[1781]: rcvd [LCP ProtRej id=0x3 80 fd 01 01 00 0c 1a 04 78 00 18 04 78 00]
Dec  6 09:37:45 achim-laptop pppd[1781]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Dec  6 09:37:45 achim-laptop pppd[1781]: Modem hangup
Dec  6 09:37:45 achim-laptop pppd[1781]: Connection terminated.


I haven't had the chance to do much since then, other than get the necessary documentation together on a USB-stick so that I can put this stuff on the forum. 

It was annoying at first (i.e. a couple of years ago). Now it is affecting my work, because I need Linux working on the net for that (JBoss and the like work easier and better under Linux and the internet is an invaluable resource). I'm mostly in hotels and short lease apartments, so I need *mobile* internet. Using Windoze and then a USB-stick to transfer data (not to mention web pages) is a real pain.

Pleeeeze, somebody out there must have an idea as to what is going on.

Any suggestions would be great.

Thanks

Achim

---

### Post by achim_59 on 2010-12-13
I got a new repy without the compression protocol stuff

From /var/log/syslog:
> 
Dec 7 19:50:07 achim-laptop chat[2540]: CONNECT
Dec 7 19:50:07 achim-laptop chat[2540]: -- got it
Dec 7 19:50:07 achim-laptop chat[2540]: send (^M)
Dec 7 19:50:07 achim-laptop pppd[2536]: Script /usr/sbin/chat -v -f /etc/chatscripts/eplus finished (pid 2539), status = 0x0
Dec 7 19:50:07 achim-laptop pppd[2536]: Serial connection established.
Dec 7 19:50:07 achim-laptop pppd[2536]: using channel 3
Dec 7 19:50:07 achim-laptop NetworkManager: SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 7 19:50:07 achim-laptop NetworkManager: SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec 7 19:50:07 achim-laptop pppd[2536]: Using interface ppp0
Dec 7 19:50:07 achim-laptop pppd[2536]: Connect: ppp0 <--> /dev/umts
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [LCP ConfReq id=0x3 <asyncmap 0x0> <auth chap MD5> <magic 0x8228888> <pcomp> <accomp>]
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [LCP ConfRej id=0x3 <magic 0x8228888>]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [LCP ConfReq id=0x4 <asyncmap 0x0> <auth chap MD5> <pcomp> <accomp>]
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [LCP ConfAck id=0x4 <asyncmap 0x0> <auth chap MD5> <pcomp> <accomp>]
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [LCP EchoReq id=0x0 magic=0x0]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [LCP DiscReq id=0x5 magic=0x8228888]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [CHAP Challenge id=0x1 <0c5dd2dd9a30db1dc6dd532142030509>, name = "UMTS_CHAP_SRVR"]
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [CHAP Response id=0x1 <a00984bbaeab0a552df8b36a82e29237>, name = "eplus"]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [LCP EchoRep id=0x0 magic=0x8228888 00 00 00 00]
Dec 7 19:50:08 achim-laptop pppd[2536]: rcvd [CHAP Success id=0x1 ""]
Dec 7 19:50:08 achim-laptop pppd[2536]: CHAP authentication succeeded
Dec 7 19:50:08 achim-laptop pppd[2536]: CHAP authentication succeeded
Dec 7 19:50:08 achim-laptop pppd[2536]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Dec 7 19:50:08 achim-laptop pppd[2536]: Modem hangup
Dec 7 19:50:08 achim-laptop pppd[2536]: Connection terminated. 


Does that help? Probaby not... but worth a try.

Achim

---

