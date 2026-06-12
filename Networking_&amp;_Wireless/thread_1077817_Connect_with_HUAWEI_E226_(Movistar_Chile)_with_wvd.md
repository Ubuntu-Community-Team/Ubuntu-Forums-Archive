---
title: "Connect with HUAWEI E226 (Movistar Chile) with wvdial"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by SLA_leandrin on 2009-02-22
Hi guys.
Just trying to make this modem work with wvdial.

I don't want to do it with vodafone mobile connect or with Escritorio Movistar, just with wvdial, but I can't make it work so far... so I need your help.

I've been googling a lot but not much infomation seems to be available.

This is my /etc/wdial.conf

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem = /dev/ttyUSB0
Phone = *99#
Idle Seconds = 300
Password = web
Modem Type = Analog Modem
Stupid Mode = 1
Compuserve = 0
Baud = 9600
Auto DNS = 0
Dial Command = ATDT
Ask Password = 0
ISDN = 0
Username = web
```

and my /etc/ppp/peers/wvdial

```
debug
noauth
defaultroute
noipdefault
usepeerdns

```

When I do

```
sudo wvdial
```

I get this;

```
leandro@linux-7p0h:~> sudo wvdial
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
--> Idle Seconds = 300, disabling automatic reconnect.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Feb 22 20:07:57 2009
--> Pid of pppd: 5209
--> Disconnecting at Sun Feb 22 20:07:58 2009
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)
```

I'm guessing this should be a silly mistake, but I can't solve it.

BTW It's for Movistar Chile!!

Cheers!

---

### Post by SLA_leandrin on 2009-02-23
Bump!!

---

### Post by GeorgeVita on 2009-02-24
Hi **SLA_leandrin**,

possibly the line that adjusts the **APN** is missing. Add the following line to your **/etc/wvdial.conf**

**Init3 = AT+CGDCONT=1,"IP","internet"**

I think you must also remove the line: **Auto DNS = 0**
and use a higher baud rate: **Baud = 115200**

Finally, as most of your lines are default with wvdial, I propose the following **/etc/wvdial.conf** file:

[B][Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = web
Password = web
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = AT+CGDCONT=1,"IP","internet"
Phone = *99#
Stupid Mode = 1
Idle Seconds = 300[/B]

I used the **Idle Seconds = 300** and your user/pass=**web** assuming you know that you need them.

My /etc/ppp/peers/wvdial is:

noauth
name wvdial
usepeerdns

I don't know if this matters!

Regards,
George

---

### Post by sraj on 2009-02-25
one other question. Can we not configure the E226 device under "mobile internet"? The device with connection is given by the same cellular service providers. Only difference being we have no idea about the APN, pin and puk values.

In my attempt to configure, I ended with a message "network not connected". In syslog, it's recorded as terminating connection because no pin provided

I ended up configuring with wvdial. But the method is complex for others at home who use my computer for connecting to internet.

---

### Post by GeorgeVita on 2009-02-25
Hi **sraj**,
as I know most Huawei 3G modems work fine with Ubuntu 8.10 and Network Manager 0.7 (I have tried E220 & E170 with a liveCD). Some users say that have problems with the SIM PIN check.

You could try again after removing the SIM PIN check by inserting the SIM card to a normal Mobile Phone, and disable this function through Phone's Menu.

Then click on the Network Manager icon, then Mobile Broadband and choose Country and Provider, finish. (hoping that system recognizes your modem)
By clicking the Network Manager icon and then your Provider you must be connected.

Regards,
George

---

### Post by sraj on 2009-02-26
well George,

The option you have provided is feasible when we are using a regular GSM/CDMA sim card with the modem. The issue over here (in India, and may be in some other countries) is that ISP provide preconfigured usb modems (NIC like E220 or EVDO like the ones from ZTE), which do not carru a sim card and users are not provided access to the device configuration interface. 

In India, we can get such devices from most of the ISP's (BSNL, Tata Indicom, Reliance et al)

The Network Manager identifies E226 immediatly and is listed as Huawei usb modem on "lsusb".

My query was whether we had an option to tell NM not to look for pin code. Or manually edit the conf file created by NM to override PIN check. I could not find the conf file in a quick search at probable locations.

I believe, this is a option which would be needed by many users and hope you agree with my view.

Regards,
Sumesh

---

### Post by SLA_leandrin on 2009-02-27
> **GeorgeVita said:**
> 
Finally, as most of your lines are default with wvdial, I propose the following **/etc/wvdial.conf** file:

[B][Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = web
Password = web
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = AT+CGDCONT=1,"IP","internet"
Phone = *99#
Stupid Mode = 1
Idle Seconds = 300[/B]


I'll give it a try and let you know, thanks!

---

### Post by mingtien on 2009-03-13
> **sraj said:**
> well George,


In India, we can get such devices from most of the ISP's (BSNL, Tata Indicom, Reliance et al)

The Network Manager identifies E226 immediatly and is listed as Huawei usb modem on "lsusb".

My query was whether we had an option to tell NM not to look for pin code. Or manually edit the conf file created by NM to override PIN check. I could not find the conf file in a quick search at probable locations.

I believe, this is a option which would be needed by many users and hope you agree with my view.

Regards,
Sumesh

Sumesh (or anyone...)

Here in Thailand we have a similar situation -- there is no card in the dongle provided by the mobile carrier.

Did you ever get an answer to this question?  I am currently using wvdial, which works 85%, but I would much rather be using Network Manager!

In case there is interest, here is the wvdial.conf that works:

[http://ubuntuforums.org/showthread.php?t=1090119](http://ubuntuforums.org/showthread.php?t=1090119)


(and by the way -- please ask Tata to send the Nano to Thailand -- we need more economical cars!)

---

### Post by saikrishna.m on 2011-05-27
hai  i am using network manage instead of wvdial this may help u also

just install latest version of ubuntu(ubuntu 10.10 or 11) .then right click on the  network manager(look beside sound icon at the top).select edit connections -select mobile broad band-click on add -if u r device detected or not(what ever the situation may be)-forward-select u r country-then select i can't find my provider and wish to enter manually option -type bsnl india -enter user name and password (if prompted so)and select connect automatically then apply.
if u r not prompted for a user name and password(ubuntu 11) just select apply.It will try to connect but fails.
then again right click on network manager icon -go to edit connection's-mobile broad band tab-u r newly created bsnl india -then edit-her u can enter u r  user name and password provided by bsnl then apply.

that's all .
left click the network manager icon - select u r new connection .
if not detect -try to enable and disable networking connections.
i have tested both in ubuntu 10.10 and 11

---

### Post by saikrishna.m on 2011-05-27
:popcorn:> **saikrishna.m said:**
> hai  i am using network manage instead of wvdial this may help u also

just install latest version of ubuntu(ubuntu 10.10 or 11) .then right click on the  network manager(look beside sound icon at the top).select edit connections -select mobile broad band-click on add -if u r device detected or not(what ever the situation may be)-forward-select u r country-then select i can't find my provider and wish to enter manually option -type bsnl india -enter user name and password (if prompted so)and select connect automatically then apply.
if u r not prompted for a user name and password(ubuntu 11) just select apply.It will try to connect but fails.
then again right click on network manager icon -go to edit connection's-mobile broad band tab-u r newly created bsnl india -then edit-her u can enter u r  user name and password provided by bsnl then apply.

that's all .
left click the network manager icon - select u r new connection .
if not detect -try to enable and disable networking connections.
i have tested both in ubuntu 10.10 and 11

---

