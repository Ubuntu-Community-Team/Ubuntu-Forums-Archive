---
title: "Motorola GPRS hangups"
date: 2006-02-16
forum: Networking &amp; Wireless
---

### Post by spedsta on 2006-02-16
I have a motorola v220, and intend using it for gprs dialup on ubuntu breezy.
So i cam here and read tazz tux's howto on installing on linux. went home and tried it numerous times, using wvdial and gnomePPP, they both have the same problem it seems. the modem hangsup. So i checked my wifes v600 3G phone, and it worked flawlessly, connecting and downloading at +- 16kbps
I hope someone can help me-- the wife moans cause i use her phone
below is various logs and console prints:

**tail -f /var/log/messages:**
Feb 16 08:21:18 localhost kernel: [4298376.157000] ohci_hcd 0000:00:02.0: wakeup
Feb 16 08:21:18 localhost kernel: [4298376.419000] usb 1-1: new full speed USB d evice using ohci_hcd and address 4
Feb 16 08:21:19 localhost kernel: [4298376.854000] usb 1-1: new full speed USB d evice using ohci_hcd and address 5
Feb 16 08:21:19 localhost kernel: [4298377.289000] usb 1-1: new full speed USB d evice using ohci_hcd and address 6
Feb 16 08:21:19 localhost kernel: [4298377.354000] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
Feb 16 08:21:20 localhost usb.agent[28618]: cdc-acm: already loaded
Feb 16 08:25:14 localhost pppd[28759]: pppd 2.4.3 started by brad, uid 1000
Feb 16 08:25:14 localhost pppd[28759]: Using interface ppp0
Feb 16 08:25:14 localhost pppd[28759]: Connect: ppp0 <--> /dev/ttyACM0
Feb 16 08:25:14 localhost pppd[28759]: PAP authentication succeeded
Feb 16 08:25:14 localhost kernel: [4298612.255000] PPP BSD Compression module registered
Feb 16 08:25:14 localhost kernel: [4298612.304000] PPP Deflate Compression module registered
Feb 16 08:25:19 localhost pppd[28759]: LCP terminated by peer (^E^@^@^J^@^@^@^@^@^@)
Feb 16 08:25:19 localhost pppd[28759]: Modem hangup
Feb 16 08:25:19 localhost pppd[28759]: Connection terminated
Feb 16 08:25:19 localhost pppd[28759]: Exit.


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**/etc/wvdial.conf**

[Dialer Defaults]

Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]

Init1 = AT+CPIN=1234

[Dialer novatel]
Modem = /dev/ttyS1
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem

[Dialer option]

Modem = /dev/tts/USB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer V220]

Modem = /dev/ttyACM0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer onboard]

Modem = /dev/ttySHSF0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer 2gonly]

Init4 = AT+COPS=0,0,"Vodacom-SA",0

[Dialer 3gonly]

Init4 = AT+COPS=0,0,"Vodacom-SA",2

[Dialer internet]

Init5 = AT+CGDCONT=1,"IP","internet";

[Dialer internetvpn]

Init5 = AT+CGDCONT=1,"IP","internetvpn";

[Dialer myapn]

Init5 = AT+CGDCONT=1,"IP","myapn"

[Dialer 384k]

Init6 = AT+CGEQMIN=1,4,64,384,64,384
Init7 = AT+CGEQREQ=1,4,64,384,64,384

[Dialer 144k]

Init6 = AT+CGEQMIN=1,4,64,144,64,144
Init7 = AT+CGEQREQ=1,4,64,144,64,144

[Dialer 64k]

Init6 = AT+CGEQMIN=1,4,64,64,64,64
Init7 = AT+CGEQREQ=1,4,64,64,64,64


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**wvdial**

brad@wells:~$ wvdial v220
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Thu Feb 16 08:25:14 2006
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.


--> pid of pppd: 28759
--> Using interface ppp0
--> pppd: Command
--> pppd: Command
--> pppd: Command
--> pppd: Command
--> pppd: Command
--> pppd: Command
--> Disconnecting at Thu Feb 16 08:25:20 2006
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.

...
---------------------------------------------------------------------------------------------------------------

Thanks in advance

---

### Post by spedsta on 2006-02-18
Problem solved!

I am posting this just in case someone runs into a similiar problem with trying to dialup with Motorola phones. The solution is to include a init string:

**Init5 = AT+CGDCONT=1,"IP","internet";**

This is already included in the wvdial.conf file, under the internet section.

So my final line looked like this

**brad@wells:~$ wvdial v220 internet**

I hope this helps anyone running into a similiar problem. I this helps send me a message :)

---

