---
title: "Connecting Sony Ericsson M600i as modem"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by djftl on 2009-05-13
Hi everyone, I'm new to Ubuntu 8.10 and I'm struggling to connect to the net. This what i have done in the terminal. I connected once and then the second it refused the connection.

code:

djftl@ubuntu:~$ lsusb
Bus 005 Device 007: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 005 Device 005: ID 04fc:0c25 Sunplus Technology Co., Ltd
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0fce:d031 Sony Ericsson Mobile Communications AB
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0a4d:008f Evolution Electronics, Ltd MK-449C Driver
Bus 001 Device 005: ID 0819:0101
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

djftl@ubuntu:~$ sudo wvdialconf
[sudo] password for djftl:
]Editing `/etc/wvdial.conf'.
Scanning your serial ports for a modem.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1 S2 S3
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyACM0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyACM0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyACM1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyACM1<*1>: ATQ0 V1 E1 -- OK
ttyACM1<*1>: ATQ0 V1 E1 Z -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM1<*1>: Modem Identifier: ATI -- Sony Ericsson M600i
ttyACM1<*1>: Speed 19200: AT -- OK
ttyACM1<*1>: Speed 38400: AT -- OK
ttyACM1<*1>: Speed 57600: AT -- OK
ttyACM1<*1>: Speed 115200: AT -- OK
ttyACM1<*1>: Speed 230400: AT -- OK
ttyACM1<*1>: Speed 460800: AT -- OK
ttyACM1<*1>: Max speed is 460800; that should be safe.
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyACM2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyACM2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyACM2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Found an USB modem on /dev/ttyACM1.
Modem configuration written to /etc/wvdial.conf.
ttyACM1<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

djftl@ubuntu:~$ sudo gedit /etc/wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","vodacom"
Stupid mode = yes
Modem Type = USB Modem
ISDN = 0
New PPPD = yes
Phone = *99***1#
Modem = /dev/ttyACM1
Username = a
Password = b
Baud = 460800

djftl@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
ATZ
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","vodacom"
AT+CGDCONT=1,"IP","vodacom"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&}5ZvV+[~
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Mon May 11 17:56:32 2009
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6116
--> Disconnecting at Mon May 11 17:56:33 2009
--> The PPP daemon has died: No root priv error (exit code = 3)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 3)
djftl@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","vodacom"
AT+CGDCONT=1,"IP","vodacom"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&}-5iU[1a][16]~
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Mon May 11 17:56:54 2009
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6122
--> Disconnecting at Mon May 11 17:56:54 2009
--> The PPP daemon has died: No root priv error (exit code = 3)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 3)
djftl@ubuntu:~$

code:
Anyone please help, i'm getting frustrated and i'm about to give up.
Thanks

---

### Post by GeorgeVita on 2009-05-13
Hi **djftl**,

at first try **sudo wvdial**
If still does not work change **Modem Type = Analog Modem**

EDIT: Also it would be better to include **AT&F** in your init2 line just to restore the factory settings of the modem. This line could be:
**Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0**

Post any other messages to follow up.

Regards,
George

---

### Post by djftl on 2009-05-13
Hi George,

Thanks for the reply,

I tried your suggestions and this what they produced:

code:

djftl@ubuntu:~$ sudo wvdial
[sudo] password for djftl:
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","vodacom"
AT+CGDCONT=1,"IP","vodacom"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&X*}3cD7~
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Wed May 13 07:31:41 2009
--> Pid of pppd: 6172
--> Disconnecting at Wed May 13 07:31:42 2009
--> The PPP daemon has died: No root priv error (exit code = 3)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 3)

djftl@ubuntu:~$ sudo gedit /etc/wvdial.conf
djftl@ubuntu:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
ATZ
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","vodacom"
AT+CGDCONT=1,"IP","vodacom"
OK
--> Modem initialized.
--> Sending: ATDT*99***2#
--> Waiting for carrier.
ATDT*99***2#
CONNECT
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&0/Z.x[~
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Wed May 13 07:37:08 2009
--> Pid of pppd: 6221
--> Disconnecting at Wed May 13 07:37:08 2009
--> The PPP daemon has died: No root priv error (exit code = 3)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 3)
djftl@ubuntu:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: **AT&F E1 V1 X1 &D2 &C1 S0=0**
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","vodacom"
AT+CGDCONT=1,"IP","vodacom"
OK
--> Modem initialized.
--> Sending: ATDT*99***2#
--> Waiting for carrier.
ATDT*99***2#
CONNECT
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&}(p}"}6(:~
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Wed May 13 07:37:54 2009
--> Pid of pppd: 6223
--> Disconnecting at Wed May 13 07:37:54 2009
--> The PPP daemon has died: No root priv error (exit code = 3)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 3)
djftl@ubuntu:~$
code:

I changed the modem type = analogue modem and added that line to reset factory settings.
I even changed that the phone nr: *99***1# to *99***2#. On windows this works fine, I'm using that now as i post.

---

### Post by GeorgeVita on 2009-05-13
Hi again.

As you are using [B]AT+CGDCONT=[COLOR="Red"]1[/COLOR],"IP","vodacom"
[/B] the dial number can be ***99#** or ***99***[COLOR="Red"]1[/COLOR]#**
In your case everything is ok (possibly your provider does not check it).

> The PPP daemon has died: No root priv error (exit code = 3)
From terminal command **man pppd** I found that this strange (for me) error is:

**3 Pppd is not setuid-root and the invoking user is not root.**

**sudo** fixed:[indent]--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> CHAP (Challenge Handshake) may be flaky.[/indent]

but not: [indent]--> The PPP daemon has died: No root priv error (exit code = 3)[/indent]

What is the exact version of Ubuntu you have?

G

---

### Post by djftl on 2009-05-13
I use Ubuntu 8.10

---

### Post by djftl on 2009-05-14
Is the anyone else that can help on this thread? George might be busy!!

---

### Post by GeorgeVita on 2009-05-14
Hi again,
... let's reply to keep this thread active!

> 3 Pppd is not setuid-root and the invoking user is not root.
as this is an error I did not faced in the past, we need some other person to help!

[B]The only possibility I can think is that you had "trim" something in the past and this changed some files (?).
[/B]
Can you try an 8.10 Live CD and use the same /etc/wvdial.conf or the following lines (copy it to a USB stick or find it into the HD):

[Dialer Defaults]
Modem = /dev/ttyACM1
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","vodacom"
Stupid mode = yes
Phone = *99***1#
Username = a
Password = b

Connect with: **sudo wvdial**

EDIT: the possible problem is that pppd needs **root privileges** not fount in your case. **You are trying to connect from a non-root user or you have change accidentally the flags in some files.** Trying with the Live CD will bypass all above (you are running always as root). A similar thread is [http://ubuntuforums.org/showthread.php?t=1035950](http://ubuntuforums.org/showthread.php?t=1035950) but the user did not answer if the test done!

NEWER EDIT: At first read **[http://www.linux.org/docs/ldp/howto/PPP-HOWTO/root.html](http://www.linux.org/docs/ldp/howto/PPP-HOWTO/root.html)**
then try from terminal window: **ls /usr/sbin/pppd -l**
this will show something like: **-rwsr-xr--  1 root dip 277352 2009-02-20 19:25 /usr/sbin/pppd**
if not similar to above try: **sudo chmod u+s /usr/sbin/pppd**
Note that in default configuration and if you are the only (& root) user it is already as above.

Regards,
George

---

### Post by djftl on 2009-05-15
thanks will try it.
Note that I can connect via live cd without even configuring anything only the dial number needs to be changed.
but will try the above.

---

