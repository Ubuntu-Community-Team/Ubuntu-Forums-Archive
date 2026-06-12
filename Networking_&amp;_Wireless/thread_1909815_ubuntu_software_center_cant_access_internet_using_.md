---
title: "ubuntu software center cant access internet using samsung SGH-E720/SGH-E840"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by asharma7001 on 2012-01-16
hi ,
i am trying to connect internet using samsung corby mate in ubuntu11.04 which shows using :

lsusb 

Bus 005 Device 005: ID 04e8:663f Samsung Electronics Co., Ltd SGH-E720/SGH-E840
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

the mobile broadband  creates a connection but can't connect internet.

mobile broadband fails to connect.

somehow on internet i found scripts to connect internet, but now only browser can access it, Ubuntu Software center does not recognize this connection as when try to install any software  it display no active internet connection..   

i am using two chatscript & connection in /etc/ppp/peers & /etc/ppp respectively..

---

### Post by jerrrys on 2012-01-17
Open a terminal and enter:

sudo apt-get update

And post any errors you get.

---

### Post by asharma7001 on 2012-01-19
thanks jerrrys for replying,
 
i used sudo apt-get update , it working..

whenever i try to install something through terminal it works successfully, but when using Ubuntu software center it sis not accessing internet.

as i said my internet connection is being used by two script which i activate by terminal thus the indicator panel does not recognize thus i think it may not also not recognize by Ubuntu software center...

---

### Post by jerrrys on 2012-01-19
I don't have any idea with whats going on between your scripts and the software center.  You may be able to use synaptic package manager until you get the problem resolved.

sudo apt-get install synaptic

goodluck

---

### Post by raja.genupula on 2012-01-19
> **asharma7001 said:**
> hi ,
i am trying to connect internet using samsung corby mate in ubuntu11.04 which shows using :

lsusb 

Bus 005 Device 005: ID 04e8:663f Samsung Electronics Co., Ltd SGH-E720/SGH-E840
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

the mobile broadband  creates a connection but can't connect internet.

mobile broadband fails to connect.

somehow on internet i found scripts to connect internet, but now only browser can access it, Ubuntu Software center does not recognize this connection as when try to install any software  it display no active internet connection..   

i am using two chatscript & connection in /etc/ppp/peers & /etc/ppp respectively..

are you sure about settings of access point ?

---

### Post by asharma7001 on 2012-01-19
> **raja.genupula said:**
> are you sure about settings of access point ?

yes i am sure ..
here are the two script 

1.) chatscript(saved in dir:/etc/ppp)  :

TIMEOUT 30
ECHO ON
ABORT '\nBUSY\r'
ABORT '\nERROR\r'
ABORT '\nNO ANSWER\r'
ABORT '\nNO CARRIER\r'
ABORT '\nNO DIALTONE\r'
ABORT '\nRINGING\r\n\r\nRINGING\r'
'' \rAT
OK 'AT+CGDCONT=1,"IP","airtelgprs.com"'
OK ATD*99#
CONNECT ""

2.) connection (saved in dir: /etc/ppp/peers) :

debug
nopcomp
noaccomp
nomagic
receive-all
noccp
novj
novjccomp
noauth
connect "/usr/sbin/chat -v -f /etc/ppp/chatscript"
usepeerdns
/dev/ttyACM0 115200
defaultroute
lcp-echo-failure 0


3.) then in terminal to connect i use :

 sudo /usr/sbin/pppd call connection

     

     now the problem is internet is access in browser & terminal very well.. but Ubuntu software center & the network manger does not recognize any active internet connection..

 any idea to sort that out will be helpful..

---

### Post by raja.genupula on 2012-01-19
Hi i think it look like a Bug .File a bug regarding this in Launchpad.
but before file a bug on it . reinstall your software center and try again . 

All the best.

---

