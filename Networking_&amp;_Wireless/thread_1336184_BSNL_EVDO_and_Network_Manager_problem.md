---
title: "BSNL EVDO and Network Manager problem"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by alokm on 2009-11-24
Hi,
I've been using a BSNL wireless EVDO connection for the last few months. I started using Ubuntu 9.04 because I did not have to do anything to connect my EVDO connection... I plugged it in and viola..!! It automatically detected it as a BSNL connection and all I had to do was to give username/ID and worked like a charm.

I recently installed Ubuntu 9.10 and I had quite a problem to get it connected....with the EVDO connection .. first it would get disconnected giving me the error in the logs as 

CHAP authentication failed: Password mismatch^M^J

which I could not google... and the next thing was that although it detected the wireless broadband connection which I created giving the username and password.... it would not connect to it and would not even let me edit the properties of the connection saying that I did not have the 'user rights'

Strangely I could delete the connection but I could not edit it..??

I have managed to get the connection working by 
1. creating a connection with only PAP authentication allowed and all others disabled.

2. disabling the option of 'Available to all users'

Can anyone tell me why the user rights are not working...
is it a bug
I am not doing something right or
I have to install some other package...

Thanks
Alok:popcorn:

---

### Post by vikramk.ibs on 2009-12-15
Can you specify which modem you are using?
There are three types of modem BSNL is providing. (according to my information)
1. USB connection modem (UT300R2U) - I have no solution for this modem.
2. LAN + WIFI Modem (UTstarcom) - The procedure is posted below, but its not working for Ubuntu 9.10
3. LAN + WIFI Modem (Nokia Siemens) - Configuration is same as UTstarcomm modem

Procedure for UTstarcom is as follows

1. Connect LAN and Set your IP to 192.168.1.xxx (xxx can be anything other than 1, max 255)

2. Go to DSL tab create new connection. Type service "**eth0**", Username <your username>, Password <your password>
Save the connection

3. The name of DSL Connection 1 will appear in the network selection list, click on it. 

4. It will disconnect the wired network (LAN) and connect Broadband.


(NOTE - This procedure fails on Ubuntu 9.10, even I am searching for solution)

for any other details, send PM to me.

---

### Post by sebinbenjamin on 2010-01-08
I believe [Alokm]("http://ubuntuforums.org/member.php?u=849860") is talking about the wireless **evdo** whereas [Vikramk.ibs]("http://ubuntuforums.org/member.php?u=661500") is talking about **wired ADSL broadband **connection. 





Note: we can get USB connection modem (UT300R2U) connected by using PPPoE mode- only draw back is a little bit security. don't worry we are using Ubuntu for that

---

### Post by Adi100 on 2010-01-08
Hi vikram.ibs,
 
if you finds the solution for this problem( wired ethernet could not be connected to internet in 9.10) please post the solution.I am also facing this problem in 9.10 whereas this problem was not present in 9.04.
 
if you happens to find the solution for connecting usb adsl modem make siemens c2110 (BSNL) using connextant viking driver(in windows)
 
lsusb identifies this device as globe span virata adsl modem.
 
do you know the commands to identify its chipset
 
thanks
 
Adi

---

### Post by sebinbenjamin on 2010-01-08
[U]Dear Adi,

I had the same problem of not getting connected after I upgraded to 9.10. What I did was to change the bridge mode into PPPoE, so that the connection is made in the modem itself. So we dont have the problem of dialing the connection, whenever the modem is turned on, it connects to net by itself. 

How to do it is given in the CD given by BSNL (if you got one). Or you could google it.


[/U][]("http://ubuntuforums.org/member.php?u=931331")

---

