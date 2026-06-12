---
title: "Wvdial and PPP daemon killed"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by Laegend on 2009-08-25
Hi Everybody!
I need an help - if is possible - because my Ubuntu 9.04 don't want work :)
 
I use my Cellphone for connect my notebook with the H3g operator.
 
This is my /etc/wvdial.conf
 
```
[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = AT+CGDCONT=1,"IP","naviga.tre.it",,0,0
ISDN = 0
Modem Type = USB Modem
Carrier Check = no
Phone = *99***1#
Username =
Password = 
```
 
And this is the output of the terminal when i try to connect
 
```
laegend@laegend-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+CGDCONT=1,"IP","naviga.tre.it",,0,0
AT+CGDCONT=1,"IP","naviga.tre.it",,0,0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Mon Aug 24 23:26:52 2009
--> Pid of pppd: 12825
--> Using interface ppp0
--> pppd: &#65533;7&#65533; &#65533;=&#65533; 
--> pppd: &#65533;7&#65533; &#65533;=&#65533; 
--> pppd: &#65533;7&#65533; &#65533;=&#65533; 
--> pppd: &#65533;7&#65533; &#65533;=&#65533; 
--> pppd: &#65533;7&#65533; &#65533;=&#65533; 
--> pppd: &#65533;7&#65533; &#65533;=&#65533; 
--> pppd: &#65533;7&#65533; &#65533;=&#65533; 
--> pppd: &#65533;7&#65533; &#65533;=&#65533; 
--> Disconnecting at Mon Aug 24 23:26:55 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```
 
Someone can tell me how to fix it?

---

### Post by GeorgeVita on 2009-08-29
Hi **Laegend**,
add a line to your /etc/wvdial.conf file:
```
Stupid Mode = yes
```
this will skip 'waiting for prompt' and continue with the ppp negotiation.

Also from network manager date I found 2 options for 3 Italia:
3 Ricaricabile: Init2 = AT+CGDCONT=1,"IP","tre.it"
3 Abbonamento: Init2 = AT+CGDCONT=1,"IP","datacard.tre.it"

Choose appropriate or ASK them!

Regards,
George

---

### Post by LtPitt on 2011-03-18
same identical problem...
Tried the fix suggested without any luck :(

---

### Post by LtPitt on 2011-03-19
I did it!

I am Italian and my only problem was that I had to use tre.it as apn :D

---

