---
title: "kppp: pppd terminates on signal 15"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by prat22 on 2010-12-14
[B]Hi!

I am using kppp in ubuntu10.10 to connect via my samsung c3010 mobile and Airtel connection. But when I dial through it, it terminates on signal 15! Some requests are rejected it seems. I am pasting the log:

[/B]    [FONT=&quot]Dec 14 20:08:02 pratik pppd[1883]: pppd 2.4.5 started by pratik, uid 1000
Dec 14 20:08:02 pratik pppd[1883]: using channel 5
Dec 14 20:08:02 pratik pppd[1883]: Using interface ppp0
Dec 14 20:08:02 pratik pppd[1883]: Connect: ppp0 <--> /dev/ttyACM0
Dec 14 20:08:02 pratik pppd[1883]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb342dae> <pcomp> <accomp>]
Dec 14 20:08:02 pratik pppd[1883]: rcvd [LCP ConfReq id=0x1 <asyncmap 0xa0000> <auth pap>]
Dec 14 20:08:02 pratik pppd[1883]: sent [LCP ConfAck id=0x1 <asyncmap 0xa0000> <auth pap>]
Dec 14 20:08:02 pratik pppd[1883]: rcvd [LCP ConfRej id=0x1 <pcomp> <accomp>]
Dec 14 20:08:02 pratik pppd[1883]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xb342dae>]
Dec 14 20:08:02 pratik pppd[1883]: rcvd [LCP ConfNak id=0x2 <asyncmap 0xa0000>]
Dec 14 20:08:02 pratik pppd[1883]: sent [LCP ConfReq id=0x3 <asyncmap 0xa0000> <magic 0xb342dae>]
Dec 14 20:08:32 pratik pppd[1883]: last message repeated 9 times
Dec 14 20:08:32 pratik pppd[1883]: Terminating on signal 15
Dec 14 20:08:32 pratik pppd[1883]: sent [LCP TermReq id=0x4 "User request"]
Dec 14 20:08:32 pratik pppd[1883]: Hangup (SIGHUP)
Dec 14 20:08:32 pratik pppd[1883]: Modem hangup
Dec 14 20:08:32 pratik pppd[1883]: Connection terminated.
Dec 14 20:08:32 pratik pppd[1883]: Exit.
[/FONT]
  

[B]I am connecting the modem over USB. The GUI shows me it is dialling the number, and then connecting to the network, and after a while ( it sends it 9 times it seems) it terminates.

Help me with this. I am struggling for three continuous days!!  ](*,)  [/B]

---

### Post by prat22 on 2010-12-15
**Anybody there? Give me something...May be a developer can answer this....**

---

### Post by alexfish on 2010-12-15
> **prat22 said:**
> **Anybody there? Give me something...May be a developer can answer this....**

MM!

What kind of film do you want developed....;)


however can look here

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

look in first post , look at lines below:

**Network Manager failing to return the NS1 and NS2**

---

### Post by prat22 on 2010-12-16
> **alexfish said:**
> MM!

What kind of film do you want developed....;)


however can look here

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

look in first post , look at lines below:

**Network Manager failing to return the NS1 and NS2**

[B]Thanks for your suggestion, but my network manager is not enabling wireless broadband! Every time I click on the checkbox in the dropdown list if nm-applet, it doesnt respond, and disables it on its own!!

The above post is regarding Kppp. It failed too! Then I tried using gnome-ppp, using wvdial, but it doesnot connect. I am unsure of the configuration of the wvdial.conf file though.

Any ideas?

I will post the log files soon.
[/B]

---

### Post by prat22 on 2010-12-16
> **alexfish said:**
> MM!

What kind of film do you want developed....;)


however can look here

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

look in first post , look at lines below:

**Network Manager failing to return the NS1 and NS2**

[B]Thanks for your suggestion, but my network manager is not enabling wireless broadband! Every time I click on the checkbox in the dropdown list if nm-applet, it doesnt respond, and disables it on its own!!
[/B][http://ubuntuforums.org/showthread.php?t=1643701](http://ubuntuforums.org/showthread.php?t=1643701)[B]

This post is regarding Kppp. It failed too! Then I tried using gnome-ppp, using wvdial, but it doesnot connect. I am unsure of the configuration of the wvdial.conf file though.

Any ideas?

I will post the log files soon.
[/B]

---

### Post by alexfish on 2010-12-16
Hi

can you try Network Manager again ,

don't use a right click , for some reason doing this with NM can disable the connection , 

have you tried using different Authentication / Configure methods in the PPP settings , by selection one method a time

---

### Post by prat22 on 2010-12-16
> **alexfish said:**
> Hi

can you try Network Manager again ,

don't use a right click , for some reason doing this with NM can disable the connection , 

have you tried using different Authentication / Configure methods in the PPP settings , by selection one method a time

[B]Yes I did! My connection doesnt require an username/password, hence, I disabled PAP/CHAP. But no results!!

I tried with wvdial, and my wvdial returned this:

[/B]    [FONT=&quot]pratik@pratik:~$ wvdial airtel
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP" "airtelgprs"
AT+CGDCONT=1,"IP" "airtelgprs"
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP" "airtelgprs"
AT+CGDCONT=1,"IP" "airtelgprs"
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP" "airtelgprs"
AT+CGDCONT=1,"IP" "airtelgprs"
ERROR
--> Bad init string.
[/FONT]
  
[B]So, I changed "airtelgprs" to "airtelgprs.com" , as it is recommended by Network manager, while it configures using wizard. This returned:

[/B]    [FONT=&quot]pratik@pratik:~$ wvdial airtel
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP" "airtelgprs.com"
AT+CGDCONT=1,"IP" "airtelgprs.com"
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP" "airtelgprs.com"
AT+CGDCONT=1,"IP" "airtelgprs.com"
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP" "airtelgprs.com"
AT+CGDCONT=1,"IP" "airtelgprs.com"
ERROR
--> Bad init string.[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]**And then I added **[/FONT]  **[FONT=&quot]"",0,0[/FONT]**[FONT=&quot]** to the init string, as suggested by a site I cant remember. This proved to get to a step closer, but with no results. It returned:**[/FONT]

[FONT=&quot][/FONT]
    [FONT=&quot]pratik@pratik:~$ wvdial airtel
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","airtelgprs.com","",0,0
AT+CGDCONT=1,"IP","airtelgprs.com","",0,0
OK
--> Modem initialized.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
pratik@pratik:~$ sudo gedit /etc/wvdial.conf
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]**Then I gave an arbitary username/password, both "airtel"**[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]pratik@pratik:~$ wvdial airtel
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","airtelgprs.com","",0,0
AT+CGDCONT=1,"IP","airtelgprs.com","",0,0
OK
--> Modem initialized.
--> Sending: ATDT*99**1*1#
--> Waiting for carrier.
ATDT*99**1*1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Thu Dec 16 16:58:32 2010
[/FONT]
  
  

[B]This showed that it needs root permissions to access /usr/sbin/pppd. So I ran it as root:

[/B]    [FONT=&quot]pratik@pratik:~$ sudo wvdial airtel
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
pratik@pratik:~$ sudo wvdial airtel
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","airtelgprs.com","",0,0
AT+CGDCONT=1,"IP","airtelgprs.com","",0,0
OK
--> Modem initialized.
--> Sending: ATDT*99**1*1#
--> Waiting for carrier.
ATDT*99**1*1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Dec 16 16:59:33 2010
--> Pid of pppd: 4450
--> Using interface ppp0
--> pppd: [/FONT][FONT=&quot]&#65533;[/FONT][FONT=&quot][15]E[08]@[0c]E[08]
--> pppd: [/FONT][FONT=&quot]&#65533;[/FONT][FONT=&quot][15]E[08]@[0c]E[08]
--> pppd: [/FONT][FONT=&quot]&#65533;[/FONT][FONT=&quot][15]E[08]@[0c]E[08]
--> pppd: [/FONT][FONT=&quot]&#65533;[/FONT][FONT=&quot][15]E[08]@[0c]E[08]
--> pppd: [/FONT][FONT=&quot]&#65533;[/FONT][FONT=&quot][15]E[08]@[0c]E[08]
--> Disconnecting at Thu Dec 16 17:00:03 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Disconnecting at Thu Dec 16 17:00:38 2010
pratik@pratik:~$ 
[/FONT]
  

[B]This is the contents of my Wvdial.conf file:

[/B]    [FONT=&quot][Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
; Phone = *99#
ISDN = 0
; Password = <Your Password>
New PPPD = yes
; Username = <Your Login Name>
Modem = /dev/ttyACM0
Baud = 460800

[Dialer airtel]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","airtelgprs.com","",0,0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = *99**1*1#
Modem = /dev/ttyACM0
Username = airtel
Dial command = ATDT
Password = airtel
Baud = 460800
Apn = airtelgprs.com
Pap = false
Chap = false

[Dialer airtel1]
Init2 = ATZ0
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP" "airtelgprs.com"
ISDN = 0
Modem = /dev/ttyACM0
Modem Type = USB Modem
Baud = 460800
[/FONT]
  
[B]Any sugessions?? It seems I am close, but.....:confused:


[/B]

---

### Post by alexfish on 2010-12-16
Hi

try 

[Dialer airtel]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyACM0
Dial command = ATDT
Baud = 460800
Dial Attempts = 3


then

sudo wvdial airtel

---

### Post by prat22 on 2010-12-16
> **alexfish said:**
> Hi

try 

[Dialer airtel]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyACM0
Dial command = ATDT
Baud = 460800
Dial Attempts = 3


then

sudo wvdial airtel


[B]Thanks, but still no result!! 
Gave your script the name "airtel2", and the result follows:[/B]

   [FONT=&quot]pratik@pratik:~$ sudo wvdial airtel2
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","airtelgprs.com"
AT+CGDCONT=1,"IP","airtelgprs.com"
OK
--> Modem initialized.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
[/FONT]

---

### Post by alexfish on 2010-12-16
hi

forgot wvdial needs username and password ,in the config (wvdial showing its age)
although airtelgprs does not require them :. hence stupid mode = 1
[http://www.sriraj.org/india/airtel-grps-apn-settings/](http://www.sriraj.org/india/airtel-grps-apn-settings/)

just add as you had in your listing

Username = airtel
Password = airtel


alexfish

---

