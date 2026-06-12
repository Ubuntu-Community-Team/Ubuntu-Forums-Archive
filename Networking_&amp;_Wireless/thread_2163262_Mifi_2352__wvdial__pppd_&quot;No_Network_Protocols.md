---
title: "Mifi 2352 / wvdial / pppd &quot;No Network Protocols runnung&quot;"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by christian2002 on 2013-07-17
Hi,

i have a problem with my Mifi 2352 UMTS Modem.
I managed to disable the useless ZeroCD and the modem is detected by Linux.

Now i tryed to connect to my provider "Vodafone".
I used wvdial, but the pppd gived up.

I used this configuration which works perfect on my Huawei E172.

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","web.vodafone.de"
Init4 = AT$QCPDPP=1,0
# Modem Type = USB Modem
Baud = 10000000
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = web
Username = web
Stupid mode = 1

```

I tryed to change the Speed, change the Modem Type Value and tryed /dev/ttyUSB1 and /dev/ttyUSB2 ,too.
But i always get the same Errors from pppd.

_**/var/log/messages**_

```
Jul 17 23:35:43 Onemini pppd[6114]: pppd 2.4.5 started by root, uid 0
Jul 17 23:35:43 Onemini pppd[6114]: speed 10000000 not supported
Jul 17 23:35:43 Onemini pppd[6114]: Using interface ppp0
Jul 17 23:35:43 Onemini pppd[6114]: Connect: ppp0 <--> /dev/ttyUSB0
Jul 17 23:35:43 Onemini pppd[6114]: CHAP authentication succeeded
Jul 17 23:35:43 Onemini pppd[6114]: CHAP authentication succeeded
Jul 17 23:36:14 Onemini pppd[6114]: [COLOR=#ff0000]IPCP: timeout sending Config-Requests[/COLOR]
Jul 17 23:36:14 Onemini pppd[6114]: Connection terminated.

```

```
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","web.vodafone.de"
AT+CGDCONT=1,"IP","web.vodafone.de"
OK
--> Sending: AT$QCPDPP=1,0
AT$QCPDPP=1,0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT HSDPA 7.2
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Jul 17 23:42:51 2013
--> Pid of pppd: 6157
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> Using interface ppp0
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> Authentication (CHAP) started
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> Authentication (CHAP) successful
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> [COLOR=#ff0000]Terminate Request (Message: "No network protocols running" )[/COLOR]
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> Disconnecting at Wed Jul 17 23:43:24 2013
--> The PPP daemon has died: Pty program error (exit code = 9)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

```

Does anyone know, what i need to do ? Do i need another Init String or is it a driver problem (Drivername "option1") ?
I can send commands to the Modem using minicom. It seems the drivers and communication with the modem ist ok.

Please  no hints like "use Wifi instead" :-) I know, the Mifi 2352 is a  Wireless Router, too. But i need the USB Modem feature of the device ;-)

Greetings,

Chris

---

### Post by christian2002 on 2013-07-19
Now i used syslog to get more information.


The first syslog is from a successful connection with my Huawei E172.
The second syslog is from my mifi, which doesnt work.




Working Huawei E172
```

Jul 19 23:11:08 Onemini pppd[5108]: pppd 2.4.5 started by root, uid 0
Jul 19 23:11:08 Onemini pppd[5108]: speed 10000000 not supported
Jul 19 23:11:08 Onemini pppd[5108]: using channel 5
Jul 19 23:11:08 Onemini pppd[5108]: Using interface ppp0
Jul 19 23:11:08 Onemini pppd[5108]: Connect: ppp0 <--> /dev/ttyUSB0
Jul  19 23:11:08 Onemini pppd[5108]: sent [LCP ConfReq id=0x1 <asyncmap  0x0> <magic 0x927537ee> <pcomp> <accomp>]
Jul  19 23:11:08 Onemini pppd[5108]: rcvd [LCP ConfReq id=0x3 <asyncmap  0x0> <auth chap MD5> <magic 0x19f1858> <pcomp>  <accomp>]
Jul 19 23:11:08 Onemini pppd[5108]: sent [LCP  ConfAck id=0x3 <asyncmap 0x0> <auth chap MD5> <magic  0x19f1858> <pcomp> <accomp>]
Jul 19 23:11:08  Onemini pppd[5108]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0>  <magic 0x927537ee> <pcomp> <accomp>]
Jul 19 23:11:08 Onemini pppd[5108]: sent [LCP EchoReq id=0x0 magic=0x927537ee]
Jul 19 23:11:08 Onemini pppd[5108]: rcvd [LCP DiscReq id=0x4 magic=0x19f1858]
Jul  19 23:11:08 Onemini pppd[5108]: rcvd [CHAP Challenge id=0x1  <e2837af962ea68daf437f41d8883858c>, name = "UMTS_CHAP_SRVR"]
Jul 19 23:11:08 Onemini pppd[5108]: sent [CHAP Response id=0x1 <4bbde41e155820d0f268488023d5937f>, name = "web"]
Jul 19 23:11:08 Onemini pppd[5108]: rcvd [LCP EchoRep id=0x0 magic=0x19f1858 92 75 37 ee]
Jul 19 23:11:08 Onemini pppd[5108]: rcvd [CHAP Success id=0x1 ""]
Jul 19 23:11:08 Onemini pppd[5108]: CHAP authentication succeeded
Jul 19 23:11:08 Onemini pppd[5108]: CHAP authentication succeeded
Jul 19 23:11:08 Onemini pppd[5108]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Jul  19 23:11:08 Onemini pppd[5108]: sent [IPCP ConfReq id=0x1 <compress  VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2  0.0.0.0>]
Jul 19 23:11:08 Onemini pppd[5108]: rcvd [LCP ProtRej id=0x5 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Jul 19 23:11:08 Onemini pppd[5108]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Jul  19 23:11:08 Onemini NetworkManager[2269]:    SCPlugin-Ifupdown: devices  added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 19  23:11:08 Onemini NetworkManager[2269]:    SCPlugin-Ifupdown: device  added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown  configuration found.
Jul 19 23:11:09 Onemini pppd[5108]: rcvd  [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns2  10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul  19 23:11:09 Onemini pppd[5108]: sent [IPCP ConfReq id=0x2 <compress  VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13>  <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins  10.11.12.14>]
Jul 19 23:11:10 Onemini pppd[5108]: rcvd [IPCP  ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>  <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 19  23:11:10 Onemini pppd[5108]: sent [IPCP ConfReq id=0x3 <compress VJ  0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2  10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 19 23:11:10 Onemini pppd[5108]: rcvd [IPCP ConfReq id=0x2]
Jul 19 23:11:10 Onemini pppd[5108]: sent [IPCP ConfNak id=0x2 <addr 0.0.0.0>]
Jul  19 23:11:10 Onemini pppd[5108]: rcvd [IPCP ConfRej id=0x3 <compress  VJ 0f 01> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul  19 23:11:10 Onemini pppd[5108]: sent [IPCP ConfReq id=0x4 <addr  0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
Jul 19 23:11:10 Onemini pppd[5108]: rcvd [IPCP ConfReq id=0x3]
Jul 19 23:11:10 Onemini pppd[5108]: sent [IPCP ConfAck id=0x3]
Jul  19 23:11:10 Onemini pppd[5108]: rcvd [IPCP ConfNak id=0x4 <addr  77.25.96.151> <ms-dns1 139.7.30.126> <ms-dns2  139.7.30.125>]
Jul 19 23:11:10 Onemini pppd[5108]: sent [IPCP  ConfReq id=0x5 <addr 77.25.96.151> <ms-dns1 139.7.30.126>  <ms-dns2 139.7.30.125>]
Jul 19 23:11:10 Onemini pppd[5108]:  rcvd [IPCP ConfAck id=0x5 <addr 77.25.96.151> <ms-dns1  139.7.30.126> <ms-dns2 139.7.30.125>]
Jul 19 23:11:10 Onemini pppd[5108]: Could not determine remote IP address: defaulting to 10.64.64.64
Jul 19 23:11:10 Onemini pppd[5108]: not replacing existing default route via 192.168.11.1
Jul 19 23:11:10 Onemini pppd[5108]: local  IP address 77.25.96.151
Jul 19 23:11:10 Onemini pppd[5108]: remote IP address 10.64.64.64
Jul 19 23:11:10 Onemini pppd[5108]: primary  DNS address 139.7.30.126
Jul 19 23:11:10 Onemini pppd[5108]: secondary DNS address 139.7.30.125
Jul 19 23:11:10 Onemini pppd[5108]: Script /etc/ppp/ip-up started (pid 5111)
Jul 19 23:11:50 Onemini pppd[5108]: Script /etc/ppp/ip-up finished (pid 5111), status = 0x0



```


Not working Mifi 2352


```

Jul 20 00:14:10 Onemini pppd[6179]: pppd 2.4.5 started by root, uid 0
Jul 20 00:14:10 Onemini pppd[6179]: speed 10000000 not supported
Jul 20 00:14:10 Onemini pppd[6179]: using channel 16
Jul 20 00:14:10 Onemini pppd[6179]: Using interface ppp0
Jul 20 00:14:10 Onemini pppd[6179]: Connect: ppp0 <--> /dev/ttyUSB0
Jul  20 00:14:10 Onemini pppd[6179]: sent [LCP ConfReq id=0x1 <asyncmap  0x0> <magic 0xa4c4b422> <pcomp> <accomp>]
Jul  20 00:14:10 Onemini pppd[6179]: rcvd [LCP ConfReq id=0x2 <asyncmap  0x0> <auth chap MD5> <magic 0x6df06138> <pcomp>  <accomp>]
Jul 20 00:14:10 Onemini pppd[6179]: sent [LCP  ConfAck id=0x2 <asyncmap 0x0> <auth chap MD5> <magic  0x6df06138> <pcomp> <accomp>]
Jul 20 00:14:10  Onemini pppd[6179]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0>  <magic 0xa4c4b422> <pcomp> <accomp>]
Jul 20 00:14:10 Onemini pppd[6179]: sent [LCP EchoReq id=0x0 magic=0xa4c4b422]
Jul 20 00:14:11 Onemini pppd[6179]: rcvd [LCP DiscReq id=0x3 magic=0x6df06138]
Jul  20 00:14:11 Onemini pppd[6179]: rcvd [CHAP Challenge id=0x1  <30abe4f4ea59a3d0a87c6494b4453451>, name = "UMTS_CHAP_SRVR"]
Jul 20 00:14:11 Onemini pppd[6179]: sent [CHAP Response id=0x1 <e0a4fa2258e376ef44a226400761cfe4>, name = "web"]
Jul 20 00:14:11 Onemini pppd[6179]: rcvd [LCP EchoRep id=0x0 magic=0x6df06138 a4 c4 b4 22]
Jul 20 00:14:11 Onemini pppd[6179]: rcvd [CHAP Success id=0x1 ""]
Jul 20 00:14:11 Onemini pppd[6179]: CHAP authentication succeeded
Jul 20 00:14:11 Onemini pppd[6179]: CHAP authentication succeeded
Jul  20 00:14:11 Onemini pppd[6179]: sent [IPCP ConfReq id=0x1 <compress  VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2  0.0.0.0>]
Jul 20 00:14:11 Onemini NetworkManager[2269]:     SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0,  iface: ppp0)
Jul 20 00:14:11 Onemini NetworkManager[2269]:     SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0,  iface: ppp0): no ifupdown configuration found.
Jul 20 00:14:12  Onemini pppd[6179]: rcvd [IPCP ConfNak id=0x1 <ms-dns1  10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13>  <ms-wins 10.11.12.14>]
Jul 20 00:14:12 Onemini pppd[6179]:  sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0>  <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins  10.11.12.13> <ms-wins 10.11.12.14>]
Jul 20 00:14:12 Onemini pppd[6179]: rcvd [IPCP ConfReq id=0xb]
Jul 20 00:14:12 Onemini pppd[6179]: sent [IPCP ConfNak id=0xb <addr 0.0.0.0>]
Jul 20 00:14:12 Onemini pppd[6179]: rcvd [IPCP ConfRej id=0x2 <compress VJ 0f 01>]
Jul  20 00:14:12 Onemini pppd[6179]: sent [IPCP ConfReq id=0x3 <addr  0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>  <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 20 00:14:12 Onemini pppd[6179]: rcvd [IPCP ConfReq id=0xc]
Jul 20 00:14:12 Onemini pppd[6179]: sent [IPCP ConfAck id=0xc]
Jul  20 00:14:12 Onemini pppd[6179]: rcvd [IPCP ConfNak id=0x3 <addr  77.24.160.200> <ms-dns1 139.7.30.125> <ms-dns2  139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:12 Onemini pppd[6179]: sent [IPCP  ConfReq id=0x4 <addr 77.24.160.200> <ms-dns1 139.7.30.125>  <ms-dns2 139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:12 Onemini pppd[6179]: rcvd [IPCP  ConfAck id=0x4 <addr 77.24.160.200> <ms-dns1 139.7.30.125>  <ms-dns2 139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:12 Onemini pppd[6179]: Received bad  configure-ack:  03 06 4d 18 a0 c8 81 06 8b 07 1e 7d 83 06 8b 07 1e 7e  82 06 8b 07 1e 7d 84 06 8b 07 1e 7e
Jul 20 00:14:15 Onemini  pppd[6179]: sent [IPCP ConfReq id=0x4 <addr 77.24.160.200>  <ms-dns1 139.7.30.125> <ms-dns2 139.7.30.126> <ms-wins  139.7.30.125> <ms-wins 139.7.30.126>]
Jul 20 00:14:15 Onemini pppd[6179]: rcvd [IPCP ConfReq id=0xd]
Jul 20 00:14:15 Onemini pppd[6179]: sent [IPCP ConfAck id=0xd]
Jul  20 00:14:15 Onemini pppd[6179]: rcvd [IPCP ConfAck id=0x4 <addr  77.24.160.200> <ms-dns1 139.7.30.125> <ms-dns2  139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:15 Onemini pppd[6179]: Received bad  configure-ack:  03 06 4d 18 a0 c8 81 06 8b 07 1e 7d 83 06 8b 07 1e 7e  82 06 8b 07 1e 7d 84 06 8b 07 1e 7e
Jul 20 00:14:18 Onemini  pppd[6179]: sent [IPCP ConfReq id=0x4 <addr 77.24.160.200>  <ms-dns1 139.7.30.125> <ms-dns2 139.7.30.126> <ms-wins  139.7.30.125> <ms-wins 139.7.30.126>]
Jul 20 00:14:18 Onemini pppd[6179]: rcvd [IPCP ConfReq id=0xe]
Jul 20 00:14:18 Onemini pppd[6179]: sent [IPCP ConfAck id=0xe]
Jul  20 00:14:18 Onemini pppd[6179]: rcvd [IPCP ConfAck id=0x4 <addr  77.24.160.200> <ms-dns1 139.7.30.125> <ms-dns2  139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:18 Onemini pppd[6179]: Received bad  configure-ack:  03 06 4d 18 a0 c8 81 06 8b 07 1e 7d 83 06 8b 07 1e 7e  82 06 8b 07 1e 7d 84 06 8b 07 1e 7e
Jul 20 00:14:21 Onemini  pppd[6179]: sent [IPCP ConfReq id=0x4 <addr 77.24.160.200>  <ms-dns1 139.7.30.125> <ms-dns2 139.7.30.126> <ms-wins  139.7.30.125> <ms-wins 139.7.30.126>]
Jul 20 00:14:21 Onemini pppd[6179]: rcvd [IPCP ConfReq id=0xf]
Jul 20 00:14:21 Onemini pppd[6179]: sent [IPCP ConfAck id=0xf]
Jul  20 00:14:21 Onemini pppd[6179]: rcvd [IPCP ConfAck id=0x4 <addr  77.24.160.200> <ms-dns1 139.7.30.125> <ms-dns2  139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:21 Onemini pppd[6179]: Received bad  configure-ack:  03 06 4d 18 a0 c8 81 06 8b 07 1e 7d 83 06 8b 07 1e 7e  82 06 8b 07 1e 7d 84 06 8b 07 1e 7e
Jul 20 00:14:24 Onemini  pppd[6179]: sent [IPCP ConfReq id=0x4 <addr 77.24.160.200>  <ms-dns1 139.7.30.125> <ms-dns2 139.7.30.126> <ms-wins  139.7.30.125> <ms-wins 139.7.30.126>]
Jul 20 00:14:24 Onemini pppd[6179]: rcvd [IPCP ConfReq id=0x10]
Jul 20 00:14:24 Onemini pppd[6179]: sent [IPCP ConfAck id=0x10]
Jul  20 00:14:24 Onemini pppd[6179]: rcvd [IPCP ConfAck id=0x4 <addr  77.24.160.200> <ms-dns1 139.7.30.125> <ms-dns2  139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:24 Onemini pppd[6179]: Received bad  configure-ack:  03 06 4d 18 a0 c8 81 06 8b 07 1e 7d 83 06 8b 07 1e 7e  82 06 8b 07 1e 7d 84 06 8b 07 1e 7e
Jul 20 00:14:27 Onemini  pppd[6179]: sent [IPCP ConfReq id=0x4 <addr 77.24.160.200>  <ms-dns1 139.7.30.125> <ms-dns2 139.7.30.126> <ms-wins  139.7.30.125> <ms-wins 139.7.30.126>]
Jul 20 00:14:27 Onemini pppd[6179]: rcvd [IPCP ConfReq id=0x11]
Jul 20 00:14:27 Onemini pppd[6179]: sent [IPCP ConfAck id=0x11]
Jul  20 00:14:27 Onemini pppd[6179]: rcvd [IPCP ConfAck id=0x4 <addr  77.24.160.200> <ms-dns1 139.7.30.125> <ms-dns2  139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:27 Onemini pppd[6179]: Received bad  configure-ack:  03 06 4d 18 a0 c8 81 06 8b 07 1e 7d 83 06 8b 07 1e 7e  82 06 8b 07 1e 7d 84 06 8b 07 1e 7e
Jul 20 00:14:30 Onemini  pppd[6179]: sent [IPCP ConfReq id=0x4 <addr 77.24.160.200>  <ms-dns1 139.7.30.125> <ms-dns2 139.7.30.126> <ms-wins  139.7.30.125> <ms-wins 139.7.30.126>]
Jul 20 00:14:30 Onemini pppd[6179]: rcvd [IPCP ConfReq id=0x12]
Jul 20 00:14:30 Onemini pppd[6179]: sent [IPCP ConfAck id=0x12]
Jul  20 00:14:30 Onemini pppd[6179]: rcvd [IPCP ConfAck id=0x4 <addr  77.24.160.200> <ms-dns1 139.7.30.125> <ms-dns2  139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:30 Onemini pppd[6179]: Received bad  configure-ack:  03 06 4d 18 a0 c8 81 06 8b 07 1e 7d 83 06 8b 07 1e 7e  82 06 8b 07 1e 7d 84 06 8b 07 1e 7e
Jul 20 00:14:33 Onemini  pppd[6179]: sent [IPCP ConfReq id=0x4 <addr 77.24.160.200>  <ms-dns1 139.7.30.125> <ms-dns2 139.7.30.126> <ms-wins  139.7.30.125> <ms-wins 139.7.30.126>]
Jul 20 00:14:33 Onemini pppd[6179]: rcvd [IPCP ConfReq id=0x13]
Jul 20 00:14:33 Onemini pppd[6179]: sent [IPCP ConfAck id=0x13]
Jul  20 00:14:33 Onemini pppd[6179]: rcvd [IPCP ConfAck id=0x4 <addr  77.24.160.200> <ms-dns1 139.7.30.125> <ms-dns2  139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:33 Onemini pppd[6179]: Received bad  configure-ack:  03 06 4d 18 a0 c8 81 06 8b 07 1e 7d 83 06 8b 07 1e 7e  82 06 8b 07 1e 7d 84 06 8b 07 1e 7e
Jul 20 00:14:36 Onemini  pppd[6179]: sent [IPCP ConfReq id=0x4 <addr 77.24.160.200>  <ms-dns1 139.7.30.125> <ms-dns2 139.7.30.126> <ms-wins  139.7.30.125> <ms-wins 139.7.30.126>]
Jul 20 00:14:36 Onemini pppd[6179]: rcvd [IPCP ConfReq id=0x14]
Jul 20 00:14:36 Onemini pppd[6179]: sent [IPCP ConfAck id=0x14]
Jul  20 00:14:36 Onemini pppd[6179]: rcvd [IPCP ConfAck id=0x4 <addr  77.24.160.200> <ms-dns1 139.7.30.125> <ms-dns2  139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:36 Onemini pppd[6179]: Received bad  configure-ack:  03 06 4d 18 a0 c8 81 06 8b 07 1e 7d 83 06 8b 07 1e 7e  82 06 8b 07 1e 7d 84 06 8b 07 1e 7e
Jul 20 00:14:39 Onemini  pppd[6179]: sent [IPCP ConfReq id=0x4 <addr 77.24.160.200>  <ms-dns1 139.7.30.125> <ms-dns2 139.7.30.126> <ms-wins  139.7.30.125> <ms-wins 139.7.30.126>]
Jul 20 00:14:39 Onemini pppd[6179]: rcvd [IPCP ConfReq id=0x15]
Jul 20 00:14:39 Onemini pppd[6179]: sent [IPCP ConfAck id=0x15]
Jul  20 00:14:39 Onemini pppd[6179]: rcvd [IPCP ConfAck id=0x4 <addr  77.24.160.200> <ms-dns1 139.7.30.125> <ms-dns2  139.7.30.126> <ms-wins 139.7.30.125> <ms-wins  139.7.30.126>]
Jul 20 00:14:39 Onemini pppd[6179]: Received bad  configure-ack:  03 06 4d 18 a0 c8 81 06 8b 07 1e 7d 83 06 8b 07 1e 7e  82 06 8b 07 1e 7d 84 06 8b 07 1e 7e
Jul 20 00:14:41 Onemini pppd[6179]: sent [LCP EchoReq id=0x1 magic=0xa4c4b422]
Jul 20 00:14:41 Onemini pppd[6179]: rcvd [LCP EchoRep id=0x1 magic=0x6df06138 a4 c4 b4 22]
Jul 20 00:14:42 Onemini pppd[6179]: IPCP: timeout sending Config-Requests
Jul 20 00:14:42 Onemini pppd[6179]: sent [LCP TermReq id=0x2 "No network protocols running"]
Jul 20 00:14:42 Onemini pppd[6179]: rcvd [LCP TermAck id=0x2]
Jul 20 00:14:42 Onemini pppd[6179]: Connection terminated.
Jul 20 00:14:42 Onemini pppd[6179]: Exit.
                                                                       

```


I hope, someone here can and want to help me

---

