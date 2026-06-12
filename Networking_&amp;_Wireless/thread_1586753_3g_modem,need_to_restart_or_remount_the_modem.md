---
title: "3g modem,need to restart or remount the modem"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by amite on 2010-10-02
Hi, I am using Huawei's 3g modem model:E1553,which was working well with ubuntu9.04 and ubuntu9.10 but when i upgraded my system to ubuntu10.04 a few days ago,i couldn't connect internet after searching alot i installed usb-modswitch and usb-modswitch-data packages after which i can connect to internet with use networkmanager applet. but some time after system startup i find network available but clicking on it doesn't do anything(for several times).For connecting to internet either i have to restart system or reinsert modem.Even if internet disconnected due to some reason then also i have to re-insert modem to connect to internet. Following are some command's output which may help to figure out my problem :
 > 
 $ dmesg | grep -e "modem" 
[   31.346902] USB Serial support registered for GSM modem (1-port)
[   31.347116] option 2-1:1.0: GSM modem (1-port) converter detected
[   31.347239] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0 
[   31.347252] option 2-1:1.1: GSM modem (1-port) converter detected
[   31.347311] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1 
[   31.347322] option 2-1:1.2: GSM modem (1-port) converter detected 
[   31.347379] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2 
[   31.347402] option: v0.7.2:USB Driver for GSM modems
 >  
$sudo wvdialconf 
[sudo] password for amitesh:  
Editing `/etc/wvdial.conf'.  Scanning your serial ports for a modem.  
Modem Port Scan: S0   S1   S2   S3
 WvModem: Cannot get information for serial port. 
ttyUSB0: ATQ0 V1 E1 -- OK 
ttyUSB0: ATQ0 V1 E1 Z -- OK
 ttyUSB0: ATQ0 V1 E1 S0=0 -- OK 
ttyUSB0: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK 
ttyUSB0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
ttyUSB0: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB0: Speed 9600: AT -- OK ttyUSB0: Max speed is 9600; that should be safe. ttyUSB0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
WvModem: Cannot get information for serial port. 
ttyUSB1: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud 
ttyUSB1: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud 
ttyUSB1: ATQ0 V1 E1 -- and failed too at 115200, giving up. 
WvModem: Cannot get information for serial port. 
ttyUSB2: ATQ0 V1 E1 -- OK ttyUSB2: ATQ0 V1 E1 Z -- OK 
ttyUSB2: ATQ0 V1 E1 S0=0 -- OK 
ttyUSB2: ATQ0 V1 E1 S0=0 &C1 -- OK 
tyUSB2: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK 
tyUSB2: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
ttyUSB2: Modem Identifier: ATI -- Manufacturer: huawei ttyUSB2: Speed 9600: AT -- OK 
ttyUSB2: Max speed is 9600; that should be safe.
ttyUSB2: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
Found a modem on /dev/ttyUSB0. Modem configuration written to /etc/wvdial.conf. ttyUSB0: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0" ttyUSB2: Speed 9600;
 init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"  
>  
~$ sudo wvdial 
--> WvDial: Internet dialer version 1.60 
--> Cannot get information for serial port. 
--> Initializing modem
--> Sending: ATZ ATZ OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 OK
 --> Sending: AT+CGDCONT=1,"IP","bsnleast" AT+CGDCONT=1,"IP","bsnleast" OK --> Modem initialized. 
--> Sending: ATDT*99# 
--> Waiting for carrier. ATDT*99# CONNECT
 --> Carrier detected.  Starting PPP immediately. 
--> Starting pppd at Sat Oct  2 21:37:46 2010 
-> Pid of pppd: 2106 
--> Using interface ppp0 
--> pppd: 0t --> pppd: 0t 
--> pppd: 0t --> pppd: 0t 
--> pppd: 0t --> pppd: 0t 
--> Disconnecting at Sat Oct  2 21:37:48 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail. 
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information. 
--> Auto Reconnect will be attempted in 5 seconds 
--> Cannot get information for serial port. 
--> Initializing modem. 
--> Sending: ATZ ATZ OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 OK 
--> Sending: AT+CGDCONT=1,"IP","bsnleast" AT+CGDCONT=1,"IP","bsnleast" OK
--> Modem initialized. 
--> Cannot get information for serial port.
--> Initializing modem. 
--> Sending: ATZ ATZ OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 OK
--> Sending: AT+CGDCONT=1,"IP","bsnleast" AT+CGDCONT=1,"IP","bsnleast" OK 
--> Modem initialized. 
--> Sending: ATDT*99#
--> Waiting for carrier. ATDT*99# CONNECT
--> Carrier detected.  Starting PPP immediately. 
--> Starting pppd at Sat Oct  2 21:37:53 2010 
--> Pid of pppd: 2111 
--> Using interface ppp0 
--> pppd: 0t --> pppd: 0t 
--> pppd: 0t --> pppd: 0t 
--> pppd: 0t --> pppd: 0t 
--> Disconnecting at Sat Oct  2 21:37:55 2010 
--> The PPP daemon has died: A modem hung up the phone (exit code = 16) 
--> man pppd explains pppd error codes in more detail. 
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information. 
--> Auto Reconnect will be attempted in 10 seconds 
--> Cannot get information for serial port. 
--> Initializing modem.
 --> Sending: ATZ ATZ OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 OK 
--> Sending: AT+CGDCONT=1,"IP","bsnleast" AT+CGDCONT=1,"IP","bsnleast" OK
 --> Modem initialized. ^CCaught signal 2:  Attempting to exit gracefully... 
--> Disconnecting at Sat Oct  2 21:37:58 2010    $sudo vi /etc/wvdial.conf 

>  
[Dialer Defaults] 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Init3 = AT+CGDCONT=1,"IP","bsnleast" Password = gprs 
Modem = /dev/ttyUSB0 
Ask Password = off 
Check Def Route = off 
Phone = *99# 
Idle Seconds = 0 
Abort on Busy = off 
Abort on No Dialtone = off 
Modem Type = Analog Modem 
Stupid Mode = on 
Baud = 9600 
Auto DNS = on 
Dial Attempts = 1 
Modem = /dev/ttyUSB0 
Init = ATZ ISDN = 0 
Username = bsnleast 
arrier Check = off 
Auto Reconnect = on 
  

while i don't have password or username for this connection so i used "Ask Password = off".I don't know what is going wrong.I just installed "wvdial" in hope it will solve my problem.  Thanks,

---

### Post by alexfish on 2010-10-02
hi

for an alternate dial up method try a  connection manager such as Sakis3g

[http://www.sakis3g.org/](http://www.sakis3g.org/)
as the name suggests it is for 3g connections, also allows optimising connections and has good logging facilities, if tried in Ubuntu download the "all in one"(usb_modeswitch ,embeded) this allows greater control over the mode-switching,therefore you could disable the installed usb_modeswitch.

they also have a forum , 

regards

alexfish

---

### Post by amite on 2010-10-03
i hv just installed sakis3g and try to connect to internet using sakis3g instead network-manager.It require "username" for connection establishment but as i already mentioned i don't have username and password for this connection and network-manager doen't require it.So, i can't connect using sakis3g script..........what should i do???

Also i am trying to figure out the problem with wvdial and one thing which is not clear to me is......

> 
part of $sudo wfdial

--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Oct  3 11:06:59 2010
--> Pid of pppd: 13855
--> Using interface ppp0
--> pppd: 04<
--> pppd: 04<
--> pppd: 04<
--> pppd: 04<
--> pppd: 04<
--> pppd: 04<
--> Disconnecting at Sun Oct  3 11:07:00 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds

why does the modem hung up?and
what does mean of "--> pppd: 04<"  ??
here is the log file(/var/log/messages) which show first disconnection of net and  then succesive try for connection.
> 
Oct  3 11:00:41 ami pppd[2293]: LCP terminated by peer
Oct  3 11:00:41 ami pppd[2293]: Connect time 62.3 minutes.
Oct  3 11:00:41 ami pppd[2293]: Sent 8660861 bytes, received 75906895 bytes.
Oct  3 11:00:41 ami pppd[2293]: Modem hangup
Oct  3 11:00:41 ami pppd[2293]: Connection terminated.
Oct  3 11:00:41 ami pppd[2293]: Terminating on signal 15
Oct  3 11:00:41 ami pppd[2293]: Exit.
Oct  3 11:06:59 ami pppd[13855]: pppd 2.4.5 started by root, uid 0
Oct  3 11:06:59 ami pppd[13855]: Using interface ppp0
Oct  3 11:06:59 ami pppd[13855]: Connect: ppp0 <--> /dev/ttyUSB0
Oct  3 11:06:59 ami pppd[13855]: CHAP authentication succeeded
Oct  3 11:06:59 ami pppd[13855]: CHAP authentication succeeded
Oct  3 11:07:00 ami pppd[13855]: Modem hangup
Oct  3 11:07:00 ami pppd[13855]: Connection terminated.
Oct  3 11:07:00 ami pppd[13855]: Exit.
Oct  3 11:07:05 ami pppd[13860]: pppd 2.4.5 started by root, uid 0
Oct  3 11:07:05 ami pppd[13860]: Using interface ppp0
Oct  3 11:07:05 ami pppd[13860]: Connect: ppp0 <--> /dev/ttyUSB0
Oct  3 11:07:05 ami pppd[13860]: CHAP authentication succeeded
Oct  3 11:07:05 ami pppd[13860]: CHAP authentication succeeded
Oct  3 11:07:07 ami pppd[13860]: Modem hangup
Oct  3 11:07:07 ami pppd[13860]: Connection terminated.
Oct  3 11:07:07 ami pppd[13860]: Exit.
Oct  3 11:07:17 ami pppd[13864]: pppd 2.4.5 started by root, uid 0
Oct  3 11:07:17 ami pppd[13864]: Using interface ppp0
Oct  3 11:07:17 ami pppd[13864]: Connect: ppp0 <--> /dev/ttyUSB0
Oct  3 11:07:17 ami pppd[13864]: CHAP authentication succeeded
Oct  3 11:07:17 ami pppd[13864]: CHAP authentication succeeded
Oct  3 11:07:19 ami pppd[13864]: Terminating on signal 15
Oct  3 11:07:19 ami pppd[13864]: Connection terminated.
Oct  3 11:07:19 ami pppd[13864]: Exit.

May i know which module is used for these connection?
Any information or suggestion is highly appreciable.......thnx :-)

---

### Post by alexfish on 2010-10-03
the only pointer in the log file is the LCP failure

try changing these setting in ppp configuration , from the terminal

Code:

[COLOR=Blue]sudo gedit /etc/ppp/options
[/COLOR] 
find the lines 
lcp-echo-failure 4
lcp-echo-interval 30

and change the values

[COLOR=Blue]lcp-echo-failure 0[/COLOR]
[COLOR=Blue]lcp-echo-interval 0[/COLOR]


then find 

[COLOR=Blue]#[/COLOR] -vj

and remove the [COLOR=Blue]#[/COLOR]

In Sakis3g you can use any username and password , if  not required , ISP does not request them , same applies to wvdial

alexfish

---

### Post by amite on 2010-10-04
thnx..

This time after system startup i tried network-manager applet and then wvdial and both failed again.So i tried Sakis3g and succeed.It's really good.:)

The only problem with Sakis3g i can see is, it doesn't show the network status as network-manager do.So i will be totally unaware of disconnecton in case of network failure.

---

### Post by alexfish on 2010-10-04
hi

visit the wiki site I think you may be surprised at what it can display and do

or if you are stuck there is a dedicated forum

regards

alexfish

---

