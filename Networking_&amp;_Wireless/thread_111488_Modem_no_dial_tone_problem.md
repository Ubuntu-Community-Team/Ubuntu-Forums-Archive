---
title: "Modem no dial tone problem"
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by mesocool on 2006-01-02
I try to connect to internet vid modem but it's shown on dial tone. The following is what I got.. Could someone help me out. Thanks you..

--------------------------------------------------:confused: 

guanyu@home:~$ sudo wvdialconf /etc/wvdial.conf
Scanning your serial ports for a modem.

Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7
Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15
Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23
Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31
Port Scan<*1>: S32  S33  S34  S35  S36  S37  S38  S39
Port Scan<*1>: S40  S41  S42  S43  S44  S45  S46  S47
Port Scan<*1>: S48  S49  S50  S51  S52  S53
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
guanyu@home:~$ sudo gedit /etc/wvdial.conf
guanyu@home:~$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT2064951000
--> Waiting for carrier.
ATDT2064951000
NO DIALTONE
--> No dial tone.
--> Disconnecting at Mon Jan  2 10:00:36 2006

---

### Post by towsonu2003 on 2006-01-13
check the phone cables carefully. also, try dialing again and again (15-20 times)... my slmodem keeps spitting errors (no dialtone, no carrier) for the first few tries... other than these, have no idea sorry...

---

### Post by cylon359 on 2006-01-13
Wait until it's done dialing, then pick up a phone and listen...

---

### Post by Mr_Grieves on 2006-01-13
[QUOTE=cylon359]Wait until it's done dialing, then pick up a phone and listen...[/QUOTE]
That demands that the phone jacks in the apartment/house is connected in a parallel manner.. not serial. Else you'll just get no dial tone in the phone you just picked up or a dail tone (wich means you just broke the connection).

---

### Post by NiTsi on 2006-03-24
[QUOTE=mesocool]I try to connect to internet vid modem but it's shown on dial tone. The following is what I got.. Could someone help me out. Thanks you..

--------------------------------------------------:confused: 

guanyu@home:~$ sudo wvdialconf /etc/wvdial.conf
Scanning your serial ports for a modem.

Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7
Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15
Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23
Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31
Port Scan<*1>: S32  S33  S34  S35  S36  S37  S38  S39
Port Scan<*1>: S40  S41  S42  S43  S44  S45  S46  S47
Port Scan<*1>: S48  S49  S50  S51  S52  S53
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
guanyu@home:~$ sudo gedit /etc/wvdial.conf
guanyu@home:~$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT2064951000
--> Waiting for carrier.
ATDT2064951000
NO DIALTONE
--> No dial tone.
--> Disconnecting at Mon Jan  2 10:00:36 2006[/QUOTE]



I have exactly the same problem in my newly installed 5.10 on my laptop. i installed sl-modem-source and sl-modem-daemon and when i wvdial i get the same. Did you find any solution finally? Please answer me [COLOR="Red"]mesocool[/COLOR] because i 'm fighting with this thing for a long time......

---

### Post by eriefisher on 2006-03-24
Don't know if this helps but it looks like your speed is set to 460800. I would change that to 115200. If the speed is to high it won't connect.

eriefisher

---

### Post by mips on 2006-03-25
You could also try and tell the modem not to wait for dialtone.

One way of doing this is via the modems Hayes AT command set.

I think ATX or ATX1 will allow for blind dialing.

[http://www.fosh.com.au/fosh/Support/su56/56KENG/ATcom.htm](http://www.fosh.com.au/fosh/Support/su56/56KENG/ATcom.htm)

---

### Post by towsonu2003 on 2006-03-25
I have sort of a similar problem in my laptop (slmodem): I have to keep re-dialing to get connected (due to No Dial Tone or No Carrier errors), and the only distro where the modem works is ubuntu (i.e. re-dialing works only in ubuntu). I have these two options enabled at the end of my wvdial.conf file:
```

Carrier Check = no
Stupid Mode = yes

```

PS. What I mean to say is: keep re-dialing to see if it works, and try putting the above options to your conf file as well.

---

### Post by mesocool on 2006-06-09
[QUOTE=NiTsi]I have exactly the same problem in my newly installed 5.10 on my laptop. i installed sl-modem-source and sl-modem-daemon and when i wvdial i get the same. Did you find any solution finally? Please answer me [COLOR="Red"]mesocool[/COLOR] because i 'm fighting with this thing for a long time......[/QUOTE]

Actually, now it works for my desktop. I just update the drivers. But for my laptop, it is still not working with no dial tone problem.. ](*,)

---

### Post by yurtboy on 2006-06-15
Did any one get anywhere with this?
I can send faxes and recieve them on the modem but calling an ISP (that I have set up before with linux) makes lots of noise but then just drops.
I will post error messages soon.

---

