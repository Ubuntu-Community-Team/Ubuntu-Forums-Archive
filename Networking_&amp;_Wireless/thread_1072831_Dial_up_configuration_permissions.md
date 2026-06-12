---
title: "Dial up configuration permissions"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by vamper on 2009-02-17
I just went through all this dial modem setup procedure not that long ago with Ubuntu 8.0.4, so now I have Kubuntu 8.1.0 also installed as another O/S on my machine, I started the set up procedure for the ext. dial up modem, once I found the terminal window -LOL, here is the result


[COLOR="DarkOrange"]hell2@Hellsbasementdoor:~$ sudo wvdialconf
[sudo] password for hell2:                
Editing `/etc/wvdial.conf'.               

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- ATQ0 V1 E1
ttyS0<*1>: failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- ATQ0 V1 E1                  
ttyS0<*1>: failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- ATQ0 V1 E1                    
ttyS0<*1>: and failed too at 115200, giving up.        
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Zoom V.90 Serial s052099g -I Z207
ttyUSB0<*1>: Speed 4800: AT -- OK
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Speed 19200: AT -- OK
ttyUSB0<*1>: Speed 38400: AT -- OK
ttyUSB0<*1>: Speed 57600: AT -- OK
ttyUSB0<*1>: Speed 115200: AT -- OK
ttyUSB0<*1>: Speed 230400: AT -- Speed 230400: AT -- OK
ttyUSB0<*1>: Speed 460800: AT -- Speed 460800: AT -- Speed 460800: AT -- Max speed is 230400; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 230400; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
hell2@Hellsbasementdoor:~$ sudo gedit wvdial.conf
sudo: gedit: command not found[/COLOR]

Ok so that was fine that I didn't know the command so I found the wvdial.conf file and set up the user name and password for the dial up connection I am using, but it would not let me save it, there was a message screen pop up that said it could not be saved and that either I did not have write permissions or there was not enough disk space - well I know there is enough disk space - so it a permission thing.

Now how do I give myself permission with Kubuntu - it is a little different to catch on to than Ubuntu

---

### Post by _duncan_ on 2009-02-17
Been a while since I used Kubuntu, but I think the default text editor is kate. Try using the following terminal command instead:
```
sudo kate /etc/wvdial.conf
```

---

### Post by vamper on 2009-02-18
> **_duncan_ said:**
> Been a while since I used Kubuntu, but I think the default text editor is kate. Try using the following terminal command instead:
```
sudo kate /etc/wvdial.conf
```
Yes that was it duncan the text editor in Kubuntu is kate

---

