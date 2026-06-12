---
title: "Dialup fails before completion"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by inschris on 2009-11-17
Greetings!  I'm a linux beginner trying to get Ubuntu 8.04 going (I have a DVD;
assume I can delay a little before switching to latest).

QU:     I will be grateful if anyone can respond:

What is wrong leading to following situation?  Am I correct in
thinking that ubuntu has connected OK with my external modem but there's
something inappropriate in the commands / responses which are
being sent to / receivd from the ISP?

SITUATION:
I'm trying to dial-up with ubuntu.  The test dial-up, using
dialer WvDial, and reflected in ENTRIES AND MSGS below,
apparently progressed OK up to a point, then failed with msg "%
Authentication failed" ; it looks as if this happened twice then
ISP cut off the connection ("carrier signal lost!").  The Linux
dialler was using correct South African number, 0860007249,
correct username (which works in Windows 2000), and correct
password (which works in Windows 2000):

...................
ENTRIES AND MSGS, 15/11/09,
AT LINUX/UBUNTU COMMAND PROMPT chris@chris-ubuntu-test:~$
(FROM MY FILE ubuntu-test.txt):

I TRIED TEST DIALUP:
chris@chris-ubuntu-test:~$ sudo wvdial --config wvdial-test
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT0860007249
--> Waiting for carrier.
ATDT0860007249
CONNECT 50666/ARQ/V90/LAPM/V42BIS
User Access Verification
Username:
--> Carrier detected.  Waiting for prompt.
Username:
--> Looks like a login prompt.
--> Sending: (username)
(username)
Password:
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed
  [ NO GOOD. SAME WITH Baud=57600  and  New PPPD = Yes
   IN WVDIAL CONFIGURATION FILE wvdial-test ]
Username:
--> Looks like a login prompt.
--> Sending: (username)
(username)
Password:
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT0860007249
--> Waiting for carrier.
NO CARRIER
ATDT0860007249
--> No Carrier!  Trying again.
--> Sending: ATDT0860007249
--> Waiting for carrier.
NO CARRIER
860007249
--> No Carrier!  Trying again.
--> Sending: ATDT0860007249
--> Waiting for carrier.
ATDT0860007249  [FOLLOWING THIS, I THINK, I ENTERED CTRL-C]
Caught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Sun Nov 15 20:39:38 2009
chris@chris-ubuntu-test:~$

.................

I LOOKED FOR INTEREST:  IN CONTRAST, LOG FROM A SUCCESSFUL
WINDOWS 2000 DIALUP / CONNECTION APPARENTLY DOESN'T MENTION
SENDING OF USERNAME AND PASSWORD
(extract from ModemLog_U.S. Robotics 56k Voice Faxmodem.txt):

11-16-2009 22:37:30.125 - Send: ATDT##########<cr>
11-16-2009 22:37:55.921 - Recv: <cr><lf>CONNECT
49333/ARQ/V90/LAPM/V42BIS<cr><lf>
11-16-2009 22:37:55.921 - Interpreted response: Connect
11-16-2009 22:37:55.921 - Connection established at 49333bps.
11-16-2009 22:37:55.921 - Error-control on.
11-16-2009 22:37:55.921 - Data compression on.
11-16-2009 22:38:25.921 - Read: Total: 621, Per/Sec: 18,
Written: Total: 1513, Per/Sec: 47
11-16-2009 22:38:40.734 - Hanging up the modem.
11-16-2009 22:38:40.734 - Hardware hangup by lowering DTR.
11-16-2009 22:38:40.843 - Detected CD dropped from lowering DTR
11-16-2009 22:38:40.843 - Recv: <cr><lf>NO CARRIER<cr><lf>
11-16-2009 22:38:40.843 - Interpreted response: No Carrier
11-16-2009 22:38:40.859 - Send: ATH<cr>

ADDITION 22/11/2009:  Greetings all!  RESOLVED:  I have now achieved dialup with minimal stress:  info per my initial post as above meant that Ubuntu had already found and identified the modem.  On 20/11/09, I had the benefit also of the valuable

 [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

and followed its suggestion System>Admin>Network.  EUREKA!  Got connection at first attempt and browsed with Firefox.

It appears that the use of wvdial on 15/11/09 wasn't a full connection attempt, it was merely a dialling test (and as such successful).  Re using wvdialer to connect, see [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer;](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer;)  I'll try it some time.

---

