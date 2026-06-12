---
title: "Glink- CDMA usb modem could connect internet"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by chitragurung on 2011-01-13
Hello,
 
I think I have configured GLink usb modem so far. But when I run wvdial command, I got the following. But I can not browse the internet. 
 
Other problem is when I try to use Gnome PPP dialer, it could not connect. Modem type is listed as ttyS0 and so on while I have setting in wvdial.conf ttyUSB0 so it does not support.
 
chitra@chitra:~$ sudo wvdial
[sudo] password for chitra: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATE0
--> Sending: ATQ0
OK
--> Re-Sending: ATE0
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATE0
--> Sending: ATQ0
OK
--> Re-Sending: ATE0
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATE0
OK
--> Sending: AT+CTA=0
OK
--> Sending: ATEOV1
NO CARRIER
OK
--> Sending: AT
OK
--> Sending: ATS0=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
CONNECT
$DCON
$DCONTYPE:2,2
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Thu Jan 13 10:59:35 2011
--> Pid of pppd: 8330
--> Using interface ppp0
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> local IP address 10.0.1.102
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> primary DNS address 202.70.64.5
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]
--> secondary DNS address 202.70.64.15
--> pppd: &#65533;[14]u&#65533;[10]&#65533;[06][08]

---

### Post by alexfish on 2011-01-13
hi

as far as I am aware , if the port is not listing.

Type the port name in the gnomeppp box(the one where the ports are listed) , then click detect

alexfish

---

### Post by chitragurung on 2011-01-13
Even If I try using Gnome PPP dialer changing port name it says can not open modem.

when I run wvdial

results is as earlier post but can not browse internet.

---

### Post by alexfish on 2011-01-14
[LIST]
[*][FONT=Verdana][SIZE=1]**Tip for the Mozzila Firefox fix ,After opening Firefox, try opening page "about:config"... Filter for "toolkit.networkmanager.disable"**[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=1]**Change the line to ....." toolkit.networkmanager.disable;true "**[/SIZE][/FONT]
[/LIST]

in gnomeppp have you put (/dev/ttyUSB0) and  the correct init codes in the configs / same as details wvdial . and checked the user and password are correct . can try to ignore detect

can post version gnomeppp

---

### Post by chitragurung on 2011-01-16
Actually, I could not browse internet. There are two problems I think.
 
1. When I run wvdial, I got message above. 
2. when I use gnome ppp dialer, after putting correct ttyUSB0  it says connecting after some time it says can not open modem.
 
How can I get gnome version information ?

---

### Post by alexfish on 2011-01-16
look in synaptic package manager

search gnome-ppp

have check this version, which lists ttyUSB*

0.3.23-1

[http://packages.debian.org/unstable/net/gnome-ppp](http://packages.debian.org/unstable/net/gnome-ppp)

---

### Post by chitragurung on 2011-01-16
Hello,
 
 
Thank you very much for your advice. So far when I run wvdial, 
 
I can get and send emails using evolution. But can not surf internet in the browser. So how can I fix it ?
 
I will try gnome ppp new version.

---

### Post by chitragurung on 2011-01-18
How to open about:config etc ?
 
Now I can send and download emails but still I can not browse internet in browser.
 
 
 
> **alexfish said:**
> 
[LIST]
[*][FONT=Verdana][SIZE=1]**Tip for the Mozzila Firefox fix ,After opening Firefox, try opening page "about:config"... Filter for "toolkit.networkmanager.disable"**[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=1]**Change the line to ....." toolkit.networkmanager.disable;true "**[/SIZE][/FONT]
[/LIST]
in gnomeppp have you put (/dev/ttyUSB0) and the correct init codes in the configs / same as details wvdial . and checked the user and password are correct . can try to ignore detect
 
can post version gnomeppp

---

### Post by alexfish on 2011-01-19
firefox screen shot in attatchements

open new page and enter the command in the box as shown / press return

click on the < ill be careful, promise > 

then filter the command

exit when done

---

### Post by chitragurung on 2011-01-26
Finally, GLINK CDMA USB modem worked with UBUNTU 8.04

---

### Post by chitragurung on 2011-03-01
Hello,

My wvdial was working in Ubuntu 8.04 after upgrading to Ubuntu 10.04 I just get the following but do not connect to internet.



--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATE0
ATE0
OK
--> Sending: AT+CTA=0
OK
--> Sending: ATEOV1
NO CARRIER
OK
--> Sending: AT
OK
--> Sending: ATS0=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
CONNECT
$DCON
$DCONTYPE:2,2
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!F} }3}"}&} } } } }#}%B#}%}'}"}(}"@$~~[7f]}#@!}!G} }3}"}&} } } } }#}%B#}%}'}"}(}"'\~~[7f]}#@!}!H} }3}"}&} } } } }#}%B#}%}'}"}(}"[7f]Y~~[7f]}#@!}!I} }3}"}&} } } } }#}%B#}%}'}"}(}"}8!~~[7f]}#@!}!J} }3}"}&} } } } }#}%B#}%}'}"}(}"  ~~[7f]}#@!}!K} }3}"}&} } } } }#}%B#}%}'}"}(}"GX~~[7f]}#@!}!L} }3}"}&} } } } }#}%B#}%}'}"}(}"P"~~[7f]}#@!}!M} }3}"}&} } } } }#}%B#}%}'}"}(}"7Z~~[7f]}#@!}!N} }3}"}&} } } } }#}%B#}%}'}"}(}"[0f][~$DORMENT
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Tue Mar  1 16:55:12 2011

---

### Post by alexfish on 2011-03-01
hi can check the links at this post by GeorgeVita

 #[**6**]("http://ubuntuforums.org/showpost.php?p=9219104&postcount=6")

regards

alexfish

---

