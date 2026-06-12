---
title: "Nokia E51 as modem"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by mauricio.ramos on 2010-02-09
Hello forum, I´ve been trying to use this cell phone (nokia e51) as a 3g modem through USB. The system detects it and after configuring some files, I can dial but the connection/modem hangs before it receives an IP and allow me to surf the web. 

I am using kubuntu 9.10 on a VirtualBox. NetworkManager detects it and shows a small cell phone icon, but after configuring and trying to activate it, it shows a message like "...activating..." and after sometime stops without network connection. This virtual machine also has a virtual network card provided by the host machine (a tap interface) that comes up at boot time as eth0 (to provide a LAN between the virtual machines and the host).

Below  goes some output. I did not copy the output of the command "lsusb" but it shows the modem and also the numbers that are provided to mobprobe in order to insert the module in the kernel. 

Thanks for any help!

=======
= dmesg =
=======

mauricio@kubuntu:/usr/sbin$ dmesg | grep -e tty
[    0.004000] console [tty0] enabled
[   14.053526] cdc_acm 2-1:1.10: ttyACM0: USB ACM device

======
= gprs =
======

lcp-echo-failure 0
lcp-echo-interval 0
nodetach
debug
show-password
connect /etc/ppp/peers/gprs-connect-chat
disconnect /etc/ppp/peers/gprs-disconnect-chat
/dev/ttyACM0
460800
crtscts
local
:10.0.0.1
noipdefault
ipcp-accept-local
defaultroute
usepeerdns
novj
nobsdcomp
novjccomp
nopcomp
noaccomp
noauth
user "brt"

===============
= gprs-connect-chat =
===============

exec chat                         \
    TIMEOUT        5                \
    ECHO         ON                \
    ABORT        '\nBUSY\r'            \
    ABORT        '\nERROR\r'            \
    ABORT        '\nNO ANSWER\r'            \
    ABORT        '\nNO CARRIER\r'        \
    ABORT        '\nNO DIALTONE\r'        \
    ABORT        '\nRINGING\r\n\r\nRINGING\r'    \
    ''        \rAT                \
    TIMEOUT        12                \
    SAY        "Press CTRL-C to close the connection at any stage!"    \
    SAY        "\ndefining PDP context...\n"    \
    OK        ATH                \
    OK        ATE1                \
    OK        'AT+CGDCONT=1,"IP","brt","",0,0'    \
    OK        ATD*99#                \
    TIMEOUT        22                \
    SAY        "\nwaiting for connect...\n"    \
    CONNECT        ""                \
    SAY        "\nConnected." \
    SAY        "\nIf the following ppp negotiations fail,\n"    \
    SAY        "try restarting the phone.\n"
        
=================
= gprs-disconnect-chat =
=================

exec /usr/sbin/chat -V -s -S    \
ABORT        "BUSY"        \
ABORT        "ERROR"        \
ABORT        "NO DIALTONE"    \
SAY        "\nSending break to the modem\n"    \
""        "\K"        \
""        "\K"        \
""        "\K"        \
""        "\d\d+++\d\dATH"    \
SAY        "\nPDP context detached\n"

=======
= dialing =
=======

root@kubuntu:/etc/ppp/peers# pppd call gprs                             
Press CTRL-C to close the connection at any stage!                      
defining PDP context...                                                 
T                                                                       
OK                                                                      
ATH                                                                     
OK                                                                      
ATE1                                                                    
OK                                                                      
AT+CGDCONT=1,"IP","brt","",0,0                                          
OK                                                                      
waiting for connect...                                                  

ATD*99#
CONNECT
Connected.
If the following ppp negotiations fail,
try restarting the phone.              

Script /etc/ppp/peers/gprs-connect-chat finished (pid 1906), status = 0x0
Serial connection established.
using channel 4
Using interface ppp0
Connect: ppp0 <--> /dev/ttyACM0
rcvd [LCP ConfReq id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xd300fe30>]
sent [LCP ConfAck id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
rcvd [LCP ConfRej id=0x1 <magic 0xd300fe30>]
sent [LCP ConfReq id=0x2 <asyncmap 0x0>]
rcvd [LCP ConfAck id=0x2 <asyncmap 0x0>]
sent [PAP AuthReq id=0x1 user="brt" password=""]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15>]
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfReq id=0x0 <addr 10.6.6.6>]
sent [IPCP ConfNak id=0x0 <addr 10.0.0.1>]
rcvd [LCP ProtRej id=0x0 80 fd 01 01 00 0c 1a 04 78 00 18 04 78 00]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [LCP TermReq id=0x1]
LCP terminated by peer
sent [LCP TermAck id=0x1]
Connection terminated.

Sending break to the modem

PDP context detached
Script /etc/ppp/peers/gprs-disconnect-chat finished (pid 1908), status = 0x0
Serial link disconnected.
Modem hangup

==============
= /var/log/mesages =
==============

Feb  8 20:18:11 kubuntu pppd[1632]: pppd 2.4.5 started by root, uid 0
Feb  8 20:18:13 kubuntu pppd[1632]: Serial connection established.
Feb  8 20:18:13 kubuntu pppd[1632]: Using interface ppp0
Feb  8 20:18:13 kubuntu pppd[1632]: Connect: ppp0 <--> /dev/ttyACM0
Feb  8 20:18:13 kubuntu pppd[1632]: PAP authentication succeeded
Feb  8 20:18:14 kubuntu pppd[1632]: LCP terminated by peer
Feb  8 20:18:17 kubuntu pppd[1632]: Connection terminated.
Feb  8 20:18:22 kubuntu pppd[1632]: Serial link disconnected.
Feb  8 20:18:22 kubuntu pppd[1632]: Modem hangup
Feb  8 20:18:22 kubuntu pppd[1632]: Exit.

---

