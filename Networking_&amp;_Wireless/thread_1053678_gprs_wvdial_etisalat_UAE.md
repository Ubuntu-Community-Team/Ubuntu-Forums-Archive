---
title: "gprs wvdial etisalat UAE"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by kharat on 2009-01-28
I am facing problem in connetting to internet using my gprs enabled mobile phone and laptop ubuntu HH.
Here is my wvdial.conf file

*Dialer Defaults*
Init = ATZ
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
Phone = 5005555
modem = /dev/ttyACM0
Username = 'etisalat'
Password = 'etisalt'
Baud = 460800
Init3 = AT+CGDCONT=1, "IP", "etisalat.ae"


from command prompt <<<wvdial>>> was run


kharat@kharat-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
NO CARRIER
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1, "IP", "etisalat.ae"
AT+CGDCONT=1, "IP", "etisalat.ae"
OK
--> Modem initialized.
--> Sending: ATDT5005555
--> Waiting for carrier.
ATDT5005555
CONNECT 9600
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT5005555
--> Waiting for carrier.
########### EMIRATES INTERNET ###########
Username: 
Username: etisalat     

--> Timed out while dialing.  Trying again.
--> Sending: ATDT5005555
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT5005555
--> Waiting for carrier.
Username: 
Username: ATDT5005555
password: 
> Your IP address is 0.0.0.0
Exiting shell, and starting PPP session.
~[7f]}#@!}!}!} }8}!}$}%\}"}&} }*} } }%}&5},TC}'}"}(}"i*~~[7f]}#@!}!}"} }8}!}$}%\}"}&} }*} } }%}&5},TC}'}"}(}"#8~~[7f]}#@!}!}#} }8}!}$}%\}"}&} }*} } }%}&5},TC}'}"}(}"j1~~[7f]}#@!}!}$} }8}!}$}%\}"}&} }*} } }%}&5},TC}'}"}(}"&[14]~~[7f]}#@!}!}%} }8}!}$}%\}"}&} }*} } }%}&5},TC}'}"}(}"o}=~~[7f]}#@!}!}&} }8}!}$}%\}"}&} }*} } }%}&5},TC}'}"}(}"%[0f]~~[7f]}#@!}!}'} }8}!}$}%\}"}&} }*} } }%}&5},TC}'}"}(}"l}&~~[7f]}#@!}!}(} }8}!}$}%\}"}&} }*} } }%}&5},TC}'}"}(}",M~~[7f]}#@!}!})} }8}!}$}%\}"}&} }*} } }%}&5},TC}'}"}(}"eD~~[7f]}#@!}!}*} }8}!}$}%\}"}&} }*} } }%}&5},TC}'}"}(}"/V~
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT5005555
--> Waiting for carrier.
ATDT5005555
CONNECT 9600
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT5005555
--> Waiting for carrier.
########### EMIRATES INTERNET ###########
Username: 
Username: 
--> Timed out while dialing.  Trying again.
--> Sending: ATDT5005555
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: ATDT5005555
--> Waiting for carrier.
Username: 
Username: ATDT5005555
password: 
> Your IP address is 0.0.0.0
Exiting shell, and starting PPP session.
~[7f]}#@!}!}!} }8}!}$}%\}"}&} }*} } }%}&wjRQ}'}"}(}"
}"~~[7f]}#@!}!}"} }8}!}$}%\}"}&} }*} } }%}&wjRQ}'}"}(}"G[10]~~[7f]}#@!}!}#} }8}!}$}%\}"}&} }*} } }%}&wjRQ}'}"}(}"}.}9~~[7f]}#@!}!}$} }8}!}$}%\}"}&} }*} } }%}&wjRQ}'}"}(}"B<~Caught signal 2:  Attempting to exit gracefully...



--> Disconnecting at Wed Jan 28 20:02:50 2009
kharat@kharat-laptop:~$

Can some one help me understanding the situation say for your ip is 0.0.0.0 and ppp start.

TIA.
Vikas Kharat.

---

### Post by ieee488 on 2009-01-29
Try adding **stupid mode = 1** and **Carrier Detect = 0** to your *wvdial.conf* file.

---

### Post by reef2dive on 2009-01-29
I had the same problem with the wireless USB modem that I am using.
It was solved at the end by setting  Stupid Mode = 1 and some additional parameters for pppd (PPPD Options) 
See the wvdial file below. (I know there are some extra things in, as this is a CDMA modem from IPWireless with connectivity issues. The AT commands are based on 3GPP standard.)

Init1 = ATE1 Z0
Init2 = AT+CGMM +CGMR
Init3 = AT+CGSN +CPOST
Init4 = AT+CPIN?
Init5 = AT+COPS=1,2,"00000"
Init6 = AT+CGATT=1,2506000
Init7 = AT+CGDCONT=1,"<Type>","<Network>","<Username>,<PWD>",0,0
Init8 = AT&F Q0 V1 &C1 &D2 S0=0 S7=60 &K3 N1 +CGATT?

Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = <PWD>
Username = <Username>
Stupid Mode = 1
PPPD Options = crtcts multilink usepeerdns lock defaultroute

---

### Post by kharat on 2009-01-30
hi ieee and reef,

My present status over the issue is as below

Success in Connection 29 Jan 2009

Below is wvdial.conf file

> [Dialer Defaults]
Init = ATZ
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
Phone = 5005555
modem = /dev/ttyACM0
Ask Password = 0
Username = 'etisalat'
Password = 'etisalt'
Baud = 460800
Init3 = AT+CGDCONT=1, "IP", "etisalat.ae"
Stupid Mode = 1



output of wvdial commnad


> kharat@kharat-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1, "IP", "etisalat.ae"
AT+CGDCONT=1, "IP", "etisalat.ae"
OK
--> Modem initialized.
--> Sending: ATDT5005555
--> Waiting for carrier.
ATDT5005555
CONNECT 9600
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Jan 29 19:36:13 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 5886
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> local  IP address 86.96.9.146
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> remote IP address 213.42.4.17
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> primary   DNS address 195.229.241.222
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> secondary DNS address 213.42.20.20
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]



Output of ifconfig command

> kharat@kharat-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:1b:4f:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:130524 (127.4 KB)  TX bytes:130524 (127.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:86.96.9.146  P-t-P:213.42.4.17  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:364 (364.0 B)  TX bytes:320 (320.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:f0:a3:5d:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:377 (377.0 B)  TX bytes:10405 (10.1 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1c:f0:a3:5d:65  
          inet addr:169.254.7.83  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-F0-A3-5D-65-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

kharat@kharat-laptop:~$ 

Failure of ping command


> kharat@kharat-laptop:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.249.91.99) 56(84) bytes of data.

--- [www.l.google.com](www.l.google.com) ping statistics ---
70 packets transmitted, 0 received, 100% packet loss, time 69011ms

kharat@kharat-laptop:~$ ping 213.42.4.146
PING 213.42.4.146 (213.42.4.146) 56(84) bytes of data.

--- 213.42.4.146 ping statistics ---
30 packets transmitted, 0 received, 100% packet loss, time 29010ms

kharat@kharat-laptop:~$ 


Output of route command

> kharat@kharat-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.42.4.17     *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     0      0        0 wlan0
default         *               0.0.0.0         U     0      0        0 ppp0
default         *               0.0.0.0         U     1000   0        0 wlan0
kharat@kharat-laptop:~$ 


utput on pressing Control C for pppd

> Caught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> Connect time 11.9 minutes.
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> Disconnecting at Thu Jan 29 19:48:27 2009
kharat@kharat-laptop:~$ 



messages in message log file

> Jan 29 19:36:14 kharat-laptop pppd[5886]: pppd 2.4.4 started by kharat, uid 1000
Jan 29 19:36:14 kharat-laptop pppd[5886]: Using interface ppp0
Jan 29 19:36:14 kharat-laptop pppd[5886]: Connect: ppp0 <--> /dev/ttyACM0
Jan 29 19:36:33 kharat-laptop pppd[5886]: PAP authentication succeeded
Jan 29 19:36:33 kharat-laptop kernel: [  516.278114] PPP BSD Compression module registered
Jan 29 19:36:33 kharat-laptop kernel: [  516.392537] PPP Deflate Compression module registered
Jan 29 19:36:34 kharat-laptop pppd[5886]: local  IP address 86.96.9.146
Jan 29 19:36:34 kharat-laptop pppd[5886]: remote IP address 213.42.4.17
Jan 29 19:36:34 kharat-laptop pppd[5886]: primary   DNS address 195.229.241.222
Jan 29 19:36:34 kharat-laptop pppd[5886]: secondary DNS address 213.42.20.20
Jan 29 19:48:27 kharat-laptop pppd[5886]: Terminating on signal 15
Jan 29 19:48:27 kharat-laptop pppd[5886]: Connect time 11.9 minutes.
Jan 29 19:48:27 kharat-laptop pppd[5886]: Sent 9882 bytes, received 7917 bytes.




As can be seen from the above that the connection stayed for some 12 minutes and there were IP addresss well also, but I couldnot ping and i DIDNOT try browsing also.
Do I need to remove PCMCIA slot wireless card in order to avoid any possible problems?

thanks and regards,
vikas

---

### Post by kharat on 2009-01-30
deleted; please refer next post

---

### Post by kharat on 2009-01-30
Present status of the issue is as below

Below is the output of wvdial command till break by Control C

> kharat@kharat-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
--> Sending: ATQ0
ATQ0
--> Re-Sending: ATZ
ATZ
OK
OK
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1, "IP", "etisalat.ae"
AT+CGDCONT=1, "IP", "etisalat.ae"
OK
--> Modem initialized.
--> Sending: ATDT5005555
--> Waiting for carrier.
ATDT5005555
CONNECT 9600
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Jan 30 11:07:18 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6569
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> local  IP address 86.96.12.27
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> remote IP address 195.229.248.10
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> primary   DNS address 195.229.241.222
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> secondary DNS address 213.42.20.20
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
Caught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> Connect time 53.6 minutes.
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]p&#65533;[06][08]
--> Disconnecting at Fri Jan 30 12:01:11 2009
kharat@kharat-laptop:~$ 
kharat@kharat-laptop:~$ 

Below is the output of ifconfig command

> kharat@kharat-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:1b:4f:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:132700 (129.5 KB)  TX bytes:132700 (129.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:86.96.12.27  P-t-P:195.229.248.10  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:284 (284.0 B)  TX bytes:240 (240.0 B)



Below is the output of route command

> kharat@kharat-laptop:~$ 


kharat@kharat-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
195.229.248.10  *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0
kharat@kharat-laptop:~$ 




> kharat@kharat-laptop:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (74.125.77.147) 56(84) bytes of data.

--- [www.l.google.com](www.l.google.com) ping statistics ---
15 packets transmitted, 0 received, 100% packet loss, time 13999ms

kharat@kharat-laptop:~$ 


Below is entries in log file

> Jan 30 11:07:18 kharat-laptop pppd[6569]: pppd 2.4.4 started by kharat, uid 1000
Jan 30 11:07:18 kharat-laptop pppd[6569]: Using interface ppp0
Jan 30 11:07:18 kharat-laptop pppd[6569]: Connect: ppp0 <--> /dev/ttyACM0
Jan 30 11:07:36 kharat-laptop pppd[6569]: PAP authentication succeeded
Jan 30 11:07:36 kharat-laptop kernel: [ 2133.607623] PPP BSD Compression module registered
Jan 30 11:07:36 kharat-laptop kernel: [ 2133.736297] PPP Deflate Compression module registered
Jan 30 11:07:38 kharat-laptop pppd[6569]: local  IP address 86.96.12.27
Jan 30 11:07:38 kharat-laptop pppd[6569]: remote IP address 195.229.248.10
Jan 30 11:07:38 kharat-laptop pppd[6569]: primary   DNS address 195.229.241.222
Jan 30 11:07:38 kharat-laptop pppd[6569]: secondary DNS address 213.42.20.20
Jan 30 11:33:00 kharat-laptop -- MARK --
Jan 30 11:53:00 kharat-laptop -- MARK --
Jan 30 12:01:10 kharat-laptop pppd[6569]: Terminating on signal 15
Jan 30 12:01:10 kharat-laptop pppd[6569]: Connect time 53.6 minutes.
Jan 30 12:01:10 kharat-laptop pppd[6569]: Sent 624451 bytes, received 2317046 bytes.


Now I can browse also. What i further did to uncheck the work offline box in MozillaFireFox. Further, I switched to auto detect the proxy setting rather than fixing it manually. 

This post is done using GSM / GPRS / LG 1800 / ETISALAT. 

The wireless card was removed from the machine for testing. Ping still not working. 


Thanks and regards,
Vikas Kharat.

---

