---
title: "Help please with connection to Internet"
date: 2005-01-14
forum: Networking &amp; Wireless
---

### Post by andrewbo on 2005-01-14
Hi

I have problem with connecting to the internet. It might dial up and connect but the 2-3 mins later the connection is dropped or it just does not connect at all. I would appreciate any help - I am sure I'm missing just a small thing but just don't seem to find it.  I have tried with pon/poff, wvdial and gnome-ppp but seem to get different results for each. here are my settings anyway:

settings in /etc/ppp/options file:

asyncmap 0
auth
crtscts
lock
hide-password
modem
passive
debug
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

Using pon/poff from command line

tail -f /var/log/messages gives me

Jan  8 19:38:00 localhost chat[5297]: NO CARRIER
Jan  8 19:38:00 localhost chat[5297]:  -- failed
Jan  8 19:38:00 localhost chat[5297]: Failed (NO CARRIER)

If the line was not plugged in I would expect this message but I can connect with Windows through this modem and line.

Using gnome-ppp from command line I get:

andrew@kestrel:~ $ sudo gnome-ppp
GNOME PPP: STDOUT: Scanning your serial ports for a modem.
GNOME PPP: STDOUT:
GNOME PPP: STDERR: ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 960 0 baud
GNOME PPP: STDERR: ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115 200 baud
GNOME PPP: STDERR: ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
GNOME PPP: STDERR: Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8
GNOME PPP: STDERR: Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16
GNOME PPP: STDERR: Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24
GNOME PPP: STDERR: Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  S32
GNOME PPP: STDERR: Port Scan<*1>: S33  S34  S35  S36  S37  S38  S39  S40
GNOME PPP: STDERR: Port Scan<*1>: S41  S42  S43  S44  S45  S46  S47  S48
GNOME PPP: STDERR: Port Scan<*1>: S49  S50  S51  S52  S53
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 -- OK
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 Z -- OK
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
GNOME PPP: STDERR: ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
GNOME PPP: STDERR: ttySL0<*1>: Speed 4800: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 9600: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 19200: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 38400: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 57600: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 115200: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 230400: AT -- OK
GNOME PPP: STDERR: ttySL0<*1>: Speed 460800: AT -- OK
GNOME PPP: STDOUT:
GNOME PPP: STDERR: ttySL0<*1>: Max speed is 460800; that should be safe.
GNOME PPP: STDOUT: Found a modem on /dev/ttySL0.
GNOME PPP: STDERR: ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
GNOME PPP: STDOUT: Modem configuration written to /dev/null.
GNOME PPP: STDERR: ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FC LASS=0"
GNOME PPP: Connecting...
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.54.0
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM1L3DT086007249
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT086007249
GNOME PPP: STDERR: BUSY
GNOME PPP: STDERR: --> The line is busy. Trying again.
GNOME PPP: STDERR: --> Sending: ATM1L3DT086007249
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT086007249
GNOME PPP: STDERR: BUSY
GNOME PPP: STDERR: --> The line is busy. Trying again.
GNOME PPP: STDERR: --> Sending: ATM1L3DT086007249
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT086007249
GNOME PPP: STDERR: BUSY
GNOME PPP: STDERR: --> The line is busy. Trying again.
GNOME PPP: STDERR: --> Sending: ATM1L3DT086007249
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT086007249
GNOME PPP: STDERR: BUSY
GNOME PPP: STDERR: --> The line is busy. Trying again.
GNOME PPP: STDERR: --> Sending: ATM1L3DT086007249
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT086007249
GNOME PPP: STDERR: BUSY
GNOME PPP: STDERR: --> The line is busy. Trying again.
GNOME PPP: STDERR: --> Sending: ATM1L3DT086007249
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT086007249
GNOME PPP: STDERR: BUSY
GNOME PPP: STDERR: --> The line is busy. Trying again.
GNOME PPP: STDERR: --> Sending: ATM1L3DT086007249
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT086007249
GNOME PPP: STDERR: BUSY
GNOME PPP: STDERR: --> The line is busy. Trying again.
GNOME PPP: STDERR: --> Sending: ATM1L3DT086007249
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT086007249
GNOME PPP: STDERR: --> Timed out while dialing.  Trying again.
GNOME PPP: STDERR: --> Maximum Attempts Exceeded..Aborting!!
GNOME PPP: STDERR: --> Disconnecting at Sat Jan  8 19:55:22 2005

I get this most times but sometimes connect but as I say it then gets dropped. Any ideas anyone ???? Thanks

---

### Post by wallijonn on 2005-01-14
> Modem Identifier: ATI -- SmartLink Soft Modem
Does this mean that you have a WinTel modem?

---

### Post by andrewbo on 2005-01-14
Yes this is a software modem but this has worked on Fedora Core 2 & 3 so I see that as being too much of a problem.

---

### Post by nocturn on 2005-01-14
[QUOTE=wallijonn]Does this mean that you have a WinTel modem?[/QUOTE]

I think it is working, as he sometimes gets a connect, but I have no experience with wintel modems.

---

### Post by nocturn on 2005-01-14
[QUOTE=andrewbo]Yes this is a software modem but this has worked on Fedora Core 2 & 3 so I see that as being too much of a problem.[/QUOTE]


I do not use dialup myself, but...
I've seen some issues with this about connections aborting because it needs something to send keep-alives.

This does not explain why there is no initial connection though.

---

