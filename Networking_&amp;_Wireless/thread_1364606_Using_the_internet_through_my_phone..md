---
title: "Using the internet through my phone."
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by lunamystry on 2009-12-26
Hi

I have been searchin and I can find ways to get internet via bluetooth But what I want is to connect my LG KS360, via usb, to my Acer aspire one running Kubuntu 9.10 or my desktop and get internet. IT worked out the box with Ubuntu 9.04. Now with Kubuntu the phone shows as modem but when I click nothing at all happens. I live in South Africa using MTN.

Thank you

---

### Post by gs777 on 2009-12-26
what is the result of this command?
"Sudo wvdialconf"
post here .

---

### Post by lunamystry on 2009-12-26
> **gs777 said:**
> what is the result of this command?
"Sudo wvdialconf"
post here .

I don't have wvdial installed.

---

### Post by gs777 on 2009-12-26
> **lunamystry said:**
> I don't have wvdial installed.

then it is a real problem. if ur phone is not recognised as a modem in nework manager applet then u have to install wvdial some way.
see if ur phone is recognised at net applet

---

### Post by lunamystry on 2009-12-26
Oh well I installed the following:
[INDENT]libxplc0.3.13
libwvstream4.6-base
libwvstream4.6-extras
libuniconf4.6
wvdial[/INDENT]
from packages.ubuntu.com downloaded them with operamini so they not too big. I ran ```
sudo wvdialconf
``` which I am guessing created the /etc/wvdial.conf file.  I then edited the /etc/wvdial.conf file using my text editor to look like this:
naa```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#Init3 = AT +COPS=0,0,"MTN-SA",3
Init3 = AT +CGDCONT=1,"IP","Internet","",0,0
Password = password
Username = username
Phone = *99#
Modem Type = Analog Modem
Stupid Mode = 1
Baud = 460800
New PPPD = yes
Dial Command = ATDT
Modem = /dev/ttyACM0
ISDN = 0
Carrier Check = no

```

I then ran ```
sudo wvdial
``` because running without sudo  gave an error about running ppp, I am guessing I am not in the ppp group or something but I like sudo wvdial so i am gonna keep it.

Thank you for the help. 
Lunamystry

---

### Post by gs777 on 2009-12-26
I have a blog on this topic [.here,]("http://stepcse.blogspot.com") u may find any help.

---

