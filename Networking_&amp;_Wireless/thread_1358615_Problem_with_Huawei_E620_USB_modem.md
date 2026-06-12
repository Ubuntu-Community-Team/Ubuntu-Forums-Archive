---
title: "Problem with Huawei E620 USB modem"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by awmian on 2009-12-18
Recently got a Huawei E620 USB modem.  The modem is detected
```
asad@asad-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 006 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
```

When I try to dial through wvdial, I keep getting the following error
```
asad@asad-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!} } }=}!}$}%x}"}&} } } } }#}%B#}%}%}&m}/!V}'}"}(}"Xe~
--> PPP negotiation detected.
--> Starting pppd at Sat Dec 19 01:34:17 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 9254
--> Using interface ppp0
--> Disconnecting at Sat Dec 19 01:34:20 2009
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)

```

Can someone please help me to get this thing started.  I have checked and rechecked my password and username and they are correct.

---

### Post by alexfish on 2009-12-18
Hi

 Which Version of Ubuntu are You using

---

### Post by awmian on 2009-12-18
I am using hardy.

Also when I tried to dial as root I think I get connected but browser does not work still

> asad@asad-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!} } }=}!}$}%x}"}&} } } } }#}%B#}%}%}&m*./}'}"}(}"3}%~
--> PPP negotiation detected.
--> Starting pppd at Sat Dec 19 02:04:09 2009
--> Pid of pppd: 11321
--> Using interface ppp0
--> local  IP address 119.154.69.252
--> remote IP address 192.168.70.1
--> primary   DNS address 203.99.163.240
--> secondary DNS address 59.103.0.90


---

### Post by alexfish on 2009-12-18
Hi

Sorry I am Not Up On Hardy

But There is A good Guide Here Worth reading

RE:Ubuntu linux on the move 

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

This One Is Worth Worth A Goole Not To Be Missed

Hope Some Hardy users Spot Your Thread

---

### Post by awmian on 2009-12-19
Ok so I have sorted out the connection thanks to the guide referred to by Alexfish. Seems I needed to set correct permissions.  However I am still unable to browse although the modem gets connected. Can someone pls help me getting this to work?
> --> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!} } }=}!}$}%x}"}&} } } } }#}%B#}%}%}&r$}; }'}"}(}"Sk~
--> PPP negotiation detected.
--> Starting pppd at Sun Dec 20 01:29:46 2009
--> Pid of pppd: 8028
--> Using interface ppp0
--> local  IP address 119.154.61.225
--> remote IP address 192.168.70.1
--> primary   DNS address 203.99.163.240
--> secondary DNS address 59.103.0.90




---

### Post by alexfish on 2009-12-20
Hi
Can you try This

dmesg | grep -e "modem" -e "tty"

ls -al /dev/ttyU* 


and post the results

Also check to see if the Modem Interface (ppp0) Shows up in the Network Tools

if not there

sudo adduser "YOURUSERNAME" dip
sudo adduser "YOURUSERNAME" dialout

Check with

Code

id

---

### Post by pdc on 2009-12-20
I suspect adding the user to the two named groups may prove valuable

---

### Post by awmian on 2009-12-22
Hey its working now.  I don't know what happened exactly.  But I followed the guide you referred me to.

> Permissions for /etc/ppp/pap-secrets and etc/ppp/chap-secrets

If you want to save the username and password in gnome-ppp they are saved in /etc/ppp/pap-secrets and etc/ppp/chap-secrets and you need to give read and write access to them from group dip - if you do not then you will get an warning message in the connection log. In most cases this does not matter as the username and password are not actually used or checked by most mobile internet providers - they know who you are from the SIM which is already registered before you can access data. Even so it is best to set these permissions. I use a root file browser which is started in a terminal by:

gksudo nautilus

You then navigate to folder /etc/ppp and right click on pap-secrets -> Properties -> Permissions tab then select dip from the drop down menu for Group and and then select read and write under Access. Repeat for chap-secrets. The annoying warning messages should now disappear.

I disabled wireless networking on my laptop and dialled up the modem. But as before couldn't browse. So I restarted my laptop and dialled the modem and voilà...its been working smoothly ever since.

Anyhow I am also posting the results you asked me to.
```
asad@asad-laptop:~$ dmesg | grep -e "modem" -e "tty"
[   11.821771] console [tty0] enabled
[   30.715453] audit(1261508312.979:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5359 profile="/usr/sbin/cupsd" namespace="default"
[   42.461379] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[   42.461434] option 5-1:1.0: GSM modem (1-port) converter detected
[   42.461636] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
[   42.461655] option 5-1:1.1: GSM modem (1-port) converter detected
[   42.461781] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
[   42.461798] option 5-1:1.2: GSM modem (1-port) converter detected
[   42.461920] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB2
[   42.461948] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
asad@asad-laptop:~$ ls -al /dev/ttyU*
crw-rw---- 1 root dialout 188, 1 2009-12-22 23:58 /dev/ttyUSB_utps_diag
crw-rw---- 1 root dialout 188, 0 2009-12-23 00:00 /dev/ttyUSB_utps_modem
crw-rw---- 1 root dialout 188, 2 2009-12-22 23:58 /dev/ttyUSB_utps_pcui

```

Thanks btw for all the help.

---

### Post by alexfish on 2009-12-22
Hi

All

Link To pap secrets

[Permissions for /etc/ppp/pap-secrets and etc/ppp/chap-secrets]("http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets")

---

### Post by pdc on 2009-12-22
Hi Awmian; pleased to hear the modem is going for you;

amongst the various things alexfish requested he suggested

> Also check to see if the Modem Interface (ppp0) Shows up in the Network Tools

if not there

sudo adduser "YOURUSERNAME" dip
sudo adduser "YOURUSERNAME" dialout

Check with

Code

id

I wondered if you had to add your username to groups dip and dialout;

and/or if you were already a member

---

