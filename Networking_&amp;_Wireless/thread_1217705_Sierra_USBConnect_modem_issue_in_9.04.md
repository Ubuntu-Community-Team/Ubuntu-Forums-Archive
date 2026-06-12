---
title: "Sierra USBConnect modem issue in 9.04"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by andyh47 on 2009-07-19
I have a Dell Mini 9 with 9.04 on which I'm trying to get to the internet using a Sierra Wireless MercuryConnect USB GSM modem.  I have been working on this a while and have tried the directions from Sierra found here:

[http://sierrawireless.custhelp.com/app/answers/detail/a_id/500](http://sierrawireless.custhelp.com/app/answers/detail/a_id/500)

and have gotten support from them, which by the way has been very good.  However, I have still not gotten a connection.... but I'm close!

I can dial the modem and connect to att and get IP addresses using Kppp and Wvdial (Network Manager and Gnome PPP don't get that far.)

I googled everything I can find on this topic but I'm still stuck.  Here's what the situation looks like:

Wvdial results:

andyh@andyh-mini:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 A0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+cgdcont=1,"IP","isp.cingular"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
CONNECT 3600000
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Jul 19 17:40:18 2009
--> Pid of pppd: 4371
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> Using interface ppp0
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> local  IP address 166.129.173.121
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> remote IP address 10.64.64.64
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> primary   DNS address 209.183.54.151
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> secondary DNS address 209.183.54.151
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11]

Here'the netstat that results:

andyh@andyh-mini:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
0.0~.0.0         0.0.0.0         0.0.0.0         U         0 0          0 ppp0

(BTW I've tried setting a default route gateway at his point as some posts suggest. That may be required but it is not sufficient.

I've tried:

~$ sudo route add default gw 10.64.64.64   (this is the remote IP address)
~$ sudo route add default gw local IP address   (which shows up in wvdial)
~$ sudo route add default ppp0
)


Here's the syslog


andyh@andyh-mini:~$ cat /var/log/syslog |tail
Jul 19 17:40:18 andyh-mini pppd[4371]: Using interface ppp0
Jul 19 17:40:18 andyh-mini pppd[4371]: Connect: ppp0 <--> /dev/ttyUSB4
Jul 19 17:40:18 andyh-mini pppd[4371]: CHAP authentication succeeded
Jul 19 17:40:18 andyh-mini pppd[4371]: CHAP authentication succeeded
Jul 19 17:40:49 andyh-mini pppd[4371]: Could not determine remote IP address: defaulting to 10.64.64.64
Jul 19 17:40:49 andyh-mini pppd[4371]: Cannot determine ethernet address for proxy ARP
Jul 19 17:40:49 andyh-mini pppd[4371]: local  IP address 166.129.173.121
Jul 19 17:40:49 andyh-mini pppd[4371]: remote IP address 10.64.64.64
Jul 19 17:40:49 andyh-mini pppd[4371]: primary   DNS address 209.183.54.151
Jul 19 17:40:49 andyh-mini pppd[4371]: secondary DNS address 209.183.54.151


Network Manager keeps writing a blank resolv.conf but taking a tip from one post, I populated it as shown but this did not solve the problem either.

resolv.conf contains:
# att
nameserver 209.183.54.151
# public servers
nameserver 67.138.54.100
nameserver 208.67.222.222

anybody know where the disconnect is?

---

### Post by GeorgeVita on 2009-07-21
Hi **andyh47**, most of your data show a connection. The only 'strange' is that your ppp is connected with the /dev/ttyUSB4 which usually reported as up to /dev/ttyUSB2. You can check **dmesg | grep ttyUSB** to find out.

A small 'fix' can be done to your /etc/wvdial.conf to skip "--> Carrier detected.  **Waiting for prompt.**"

**sudo gedit /etc/wvdial.conf**

Add line: **Stupid Mode = 1**

From the following the 'disconnection' is not shown:> **andyh47 said:**
> ...andyh@andyh-mini:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 A0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+cgdcont=1,"IP","isp.cingular"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
CONNECT 3600000
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Jul 19 17:40:18 2009
--> Pid of pppd: 4371
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> Using interface ppp0
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> local  IP address 166.129.173.121
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> remote IP address 10.64.64.64
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> primary   DNS address 209.183.54.151
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11] 
--> secondary DNS address 209.183.54.151
--> pppd: &#65533;w[11] [10]&#65533;[11]  x[11]

Usually Firefox starts in 'offline mode' when using **wvdial**. If so use **ALT-F W** to remove it and try browsing.

Finally, post your /etc/wvdial.conf together with the lines from **dmesg | grep ttyUSB** to follow up.

Regards,
George

---

### Post by andyh47 on 2009-07-21
George, Thanks for the help...

Firefox did come up in offline mode. That may have been an issue.  I put it in online mode and after restoring my resolv.conf that network manager keeps erasing, Firefox gave a busy indicator for a while before coming back with address not found.  Not much but it looks like progress to me.


Here's the wvdial.conf

andyh@andyh-mini:/etc$ cat wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 A0=0 &C1 &D2 +FCLASS=0
Init3 = AT+cgdcont=1,"IP","isp.cingular"
Stupid Mode = 1
Modem Type = USB Modem
Baud = 300000
New PPPD = yes
Modem = /dev/ttyUSB4
ISDN = 0
Phone = *99***1#
Password =' '
Username =' '
andyh@andyh-mini:/etc$

Here's the dmesg

andyh@andyh-mini:/etc$ dmesg | grep ttyUSB
[  735.899196] usb 1-1: Sierra USB modem converter now attached to ttyUSB0
[  735.902577] usb 1-1: Sierra USB modem converter now attached to ttyUSB1
[  735.906654] usb 1-1: Sierra USB modem converter now attached to ttyUSB2
[  735.911544] usb 1-1: Sierra USB modem converter now attached to ttyUSB3
[  735.914816] usb 1-1: Sierra USB modem converter now attached to ttyUSB4
[  735.918605] usb 1-1: Sierra USB modem converter now attached to ttyUSB5
[  735.922710] usb 1-1: Sierra USB modem converter now attached to ttyUSB6

I worked with sierra wireless support.  Here's what they said about the USBConnect modem is this regard:

[INDENT]Please be aware the connection can be made on ttyUSB3. However, the Data port is actually ttyUSB4 ( I noticed that wvdial detects it, as well)
In short - ttyUSB3 is the AT/Data port and the ttyUSB4 is the data port
=
To send AT commands you can use ttyUSB3. Open a minicom session with the modem and check the status of the modem

APN=
at+cgdcont?
at+cgdcont=1,"IP","isp.cingular" - is the default APN for Mercury device
Set the connection to 2G to test the results
at!band=4 >> it answers ok
=

[/INDENT]Here's a whole wvdial session with the disconnect shown:


--> Auto Reconnect will be attempted in 10 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 A0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+cgdcont=1,"IP","isp.cingular"
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 A0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+cgdcont=1,"IP","isp.cingular"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
CONNECT 3600000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Jul 21 16:16:38 2009
--> Pid of pppd: 4697
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> Using interface ppp0
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> local  IP address 166.129.18.239
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> remote IP address 10.64.64.64
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> primary   DNS address 209.183.54.151
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> secondary DNS address 209.183.54.151
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
^CCaught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> Connect time 27.9 minutes.
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> pppd: Ôø&#937;Ôø&#937;E[08]Ôø&#937;Ôø&#937;E[08] Ôø&#937;E[08]
--> Disconnecting at Tue Jul 21 16:44:32 2009

---

### Post by andyh47 on 2009-07-24
After an unbelievable number of hours hacking at this I came across this post.

[http://docs.google.com/Doc?id=d9khzpw_0w4m774dd](http://docs.google.com/Doc?id=d9khzpw_0w4m774dd).

which solved the problem.


Now Network Manager recognizes the modem and also connects.

---

### Post by kgarbutt on 2009-07-25
Hi Andy,

I just wanted to tell you that my AT&T Sierra USBConnent Mercury device worked perfectly in my ASUS eeepc 701 running Jaunty 9.04. The kernel recongized it as soon as I plugged it in. Actually I am write this post with now as we speak.

Anyways, good luck ith your connection. I just wanted you to know that it shoould work. Good luck.

Ken

---

