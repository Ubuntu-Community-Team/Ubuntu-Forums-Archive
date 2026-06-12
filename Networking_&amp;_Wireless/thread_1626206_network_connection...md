---
title: "network connection.."
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by khatikbbdn72 on 2010-11-20
hie everyone,
 i searched it hard at google.. and found some solution but none of them worked 

problems--

1)i have micromax 372g usb modem(3g).. but it is not being connected ubuntu 10.10

2)
i suppose my device is being recognised.. and i tried this method

[http://www.harshj.com/2010/03/22/using-the-bsnl-3g-data-card-on-linux/comment-page-1/#comment-75541](http://www.harshj.com/2010/03/22/using-the-bsnl-3g-data-card-on-linux/comment-page-1/#comment-75541)

but when i tried to install, it said that package missing for wvdial.. what should i do.. where can i get this package and how can i install it (with no dependany check)

guys, if u have other solution apart from other.. then thats most welcome, my life is extremely difficult without internet on ubuntu, i am reday to give anyother information that u need

i have ubuntu 10.10 maverick dual boot with windows.

 and yes take into consideration that i dont have internet on ubuntu.. so provide me full detail how to install it from other media.. and commands to execute them


thanx in advance

---

### Post by jrev on 2010-11-20
What will be the use of Ubuntu if you have no Internet connection ?

---

### Post by khatikbbdn72 on 2010-11-20
well i do have internet connection but its usb adapter connection that i am trying to resolve;
read my question first plz.. and i do have connection on windows that i can use to install some softwares required for wvdial package etc..
and i can make my life simpler..
and i use this adpater micromax372g( 3g )perfectoly on my windoows

---

### Post by dineshs on 2010-11-20
Did you try the Mobile broadband tab in Network manager?(Right click Network manager icon on right top of the panel -click edit connections.....)
Did you try pppconfig command ([http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html))

---

### Post by khatikbbdn72 on 2010-11-20
@dineshs, thanx for reply dineshs....
let me check your link.. and let you know the result

---

### Post by dineshs on 2010-11-20
You may also try post count #2 in
[http://ubuntuforums.org/showthread.php?t=1223769](http://ubuntuforums.org/showthread.php?t=1223769)

---

### Post by khatikbbdn72 on 2010-11-20
hi dinesh,
i tried my level best to do what it said in your first link, but i could not manage to connnect my usb with *gnome-ppt*  ..

now i went for your last link.. now after installing those five packages in row, i am not quite able to understand the code written there and how to save that code and where to save that code.. i will be highly pleased if you could make my life simpler with those codes and what are the commands to save them.. thnx for your kind help.. waiting fro your reply

---

### Post by khatikbbdn72 on 2010-11-20
[http://ubuntuforums.org/showthread.php?t=1439356&page=3](http://ubuntuforums.org/showthread.php?t=1439356&page=3)

regarding above link i have the same problem, even i have 372g modem micromax.. modeswitch and all what these stuff are.
and to amke it quick i have installed modeswitch, but how can i know either its done its work or not?

---

### Post by dineshs on 2010-11-20
Please post what you get for
```
dmesg | grep -e "modem" -e "tty" 
```
> now after installing those five packages in row, i am not quite able to understand the code written there and how to save that code and where to save that code.. i will be highly pleased if you could make my life simpler with those codes and what are the commands to save them.
After installing wvdial run```
wvdialconf
```and post the result of```
cat /etc/widial.conf 
```

---

### Post by dineshs on 2010-11-20
Please post what you get for
```
dmesg | grep -e "modem" -e "tty" 
```
> now after installing those five packages in row, i am not quite able to understand the code written there and how to save that code and where to save that code.. i will be highly pleased if you could make my life simpler with those codes and what are the commands to save them.
After installing wvdial run```
wvdialconf
```and post the result of```
cat /etc/widial.conf 
```

---

### Post by dineshs on 2010-11-20
Please post what you get for
```
dmesg | grep -e "modem" -e "tty" 
```
> now after installing those five packages in row, i am not quite able to understand the code written there and how to save that code and where to save that code.. i will be highly pleased if you could make my life simpler with those codes and what are the commands to save them.
After installing wvdial run```
wvdialconf
```and post the result of```
cat /etc/widial.conf 
```

---

### Post by khatikbbdn72 on 2010-11-21
result of code:

dmesg | grep -e "modem" -e "tty"
atul@atul-home:~$ dmesg |grep -e"modem" -e"tty"
[    0.000000] console [tty0] enabled
[    0.221909] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.222023] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.222440] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.222605] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  422.798821] USB Serial support registered for GSM modem (1-port)
[  422.801037] option: v0.7.2:USB Driver for GSM modems
[  422.802555] option 1-6:1.0: GSM modem (1-port) converter detected
[  422.805097] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[  422.805158] option 1-6:1.1: GSM modem (1-port) converter detected
[  422.807091] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[  422.807154] option 1-6:1.3: GSM modem (1-port) converter detected
[  422.809737] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
atul@atul-home:~$ 


result of code:

cat /etc/widial.conf

01    [Dialer bsnlnet]
02    Modem Type = Analog Modem
03    Phone = *99#
04    ISDN = 0
05    Baud = 460800
06    Username = " "
07    Password = " "
08    Modem = /dev/ttyUSB1
09    Init1 = ATZ
10    Init2 = at+cgdcont=1,"ip","bsnlnet"
11    Stupid Mode = 1
atul@atul-home:~$

---

### Post by khatikbbdn72 on 2010-11-21
result of 

wvdialconf


Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: Micromax
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: Micromax
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB1.
/etc/wvdial.conf<Warn>: Ignoring malformed input line: "01 [Dialer bsnlnet]"
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp1874': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
atul@atul-home:~$

---

### Post by khatikbbdn72 on 2010-11-21
this is the result that i got when i changed my wvdialconf file  to that given in post 6


--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

---

### Post by dineshs on 2010-11-21
Run```
sudo gedit /etc/widial.conf
```and edit the file as in post#10 ([COLOR="Red"]those serial nos before each line not required[/COLOR]).I mean it should be similar to> [Dialer Defaults] 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Init3 = AT+CGDCONT=1,,"bsnlnet" 
Stupid Mode = 1
Modem Type = Analog Modem 
ISDN = 0 
New PPPD = yes 
Phone = *99***1# 
Modem = /dev/ttyUSB1 
Username = 
Password = 
Baud = 115200 
Note: substitute your values for user id and password
Now run ```
sudo wvdial
``` and see if there is any difference
I think your connection will surely work if you edit /etc/widial.conf properly (may require a trial and error or google search).For example you can try Modem = /dev/ttyUSB0 or Modem = /dev/ttyUSB2  instead of [COLOR="Blue"]Modem = /dev/ttyUSB1 [/COLOR]

---

### Post by khatikbbdn72 on 2010-11-22
thanx for the reply dinesh.. 
well i am searching hard at google and still with no solution, coming back to point.. now i used the settings provided by you wvdialcong and when try to connect with

sudo wvdial


--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,,"bsnlnet"
AT+CGDCONT=1,,"bsnlnet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
--> Disconnecting at Sun Nov 21 23:45:51 2010
root@atul-home:~# 

i tried changing usb0 or usb1, but its being detected at usb1. so thts out of question..

well i got 1 thing in comman that it always comes with "cannot get information for serial port"
can i get something out out of it.. and what about above result

---

### Post by khatikbbdn72 on 2010-11-22
and plz help me hear [http://ubuntuforums.org/showthread.php?t=1628124](http://ubuntuforums.org/showthread.php?t=1628124)

---

### Post by khatikbbdn72 on 2010-11-22
hie everyone..

i am searching hard at google but still with no solution..

i have micromax 372g usb maodem (3g) that has onboard driver.. but i am not able to use it on ubuntu 10.10 maverick, i tried modeswitch, wvdial and stuff plz help..
i am finding myself nowhere without internet

i started a thread in beginner corner and check all what i have done... plz visit this page and reply....

[http://ubuntuforums.org/showthread.php?t=1626206](http://ubuntuforums.org/showthread.php?t=1626206)

---

### Post by halj32 on 2010-11-22
have you tried installing usb-modeswitch & usb-modeswitch-data
worked for me
also try using network manager instead of wvdial

have a look at these sites
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

[http://www.sakis3g.org/](http://www.sakis3g.org/)
they might help

re multimedia try installing ffmpeg or win32 codecs, when your online run this in a terminal & then install win32, if you want to watch dvd's install libdvdcss2

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update


goodluck

I was wondering what network & where you are & found this
[http://www.freetechy.com/bsnl/bsnl-internet-settings-t38.html](http://www.freetechy.com/bsnl/bsnl-internet-settings-t38.html)

---

### Post by uRock on 2010-11-22
Have you tried installing the Linux firmware package? If no, then run this command in a terminal to install the package.```
sudo apt-get install linux-firmware-nonfree
```my USB wireless started working as soon as I installed that package and it has worked for a few others that I have given that advice to, so I am hoping it works for you, too.

Let us know if this worked.

---

### Post by halj32 on 2010-11-22
> **uRock said:**
> Have you tried installing the Linux firmware package? If no, then run this command in a terminal to install the package.```
sudo apt-get install linux-firmware-nonfree
```my USB wireless started working as soon as I installed that package and it has worked for a few others that I have given that advice to, so I am hoping it works for you, too.

Let us know if this worked.

I thought that linux-firmware-nonfree contains firmware for DVB cards not 3G dongles.

see
[http://packages.ubuntu.com/karmic/linux-firmware-nonfree](http://packages.ubuntu.com/karmic/linux-firmware-nonfree)

---

### Post by khatikbbdn72 on 2010-11-24
@urock 

i dnt think there is need to run this code if you have .deb file, anyways i installed your utility but still came with no solution...

@halz32,

well. u know biggest problem that comes with an offline user is.. they donot get packages for any new utility like "sakis3g".. thanx for suggestion... but i will prefer to have basic solution.. 
i dnt think "sakis3g" is any bettar than gnomeppp..
that i already installed, anyother solution is highly welcomed
thanx in advance

---

### Post by dineshs on 2010-11-27
> **khatikbbdn72 said:**
> 
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
--> Disconnecting at Sun Nov 21 23:45:51 2010
i tried changing usb0 or usb1, but its being detected at usb1. so thts out of question..
Add this line to wvdial.conf (You may fix usb1)
```
Carrier Check = no
```
Ref:[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9%20errors%20dialup](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9%20errors%20dialup)

---

### Post by khatikbbdn72 on 2010-12-10
thnx for your reply, snd i did carrier check =no..
but still wid no success..
feels like i will never be able to connect this device to ubuntu
recently i easily connected n72 via wvdial.. is this the driver issue that is inbuild in my usb device..?

---

