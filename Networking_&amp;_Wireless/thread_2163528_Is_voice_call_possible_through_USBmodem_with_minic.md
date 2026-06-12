---
title: "Is voice call possible through USBmodem with minicom?"
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by bkpsusmitaa on 2013-07-18
I have a Huawei modem which I can use to log on to internet with the following wvdial configuration. Is it possible for me to call, or send SMS to, any phone no. with the modem using minicom abd AT commands?
Phone = *99#
Username = username
Password = password
Authentication Type = normal
Proxy = Enable
Proxy address = 192.168.035.201
Port = 8081
Stupid Mode = 1
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = AT+CGDCONT=1,"IP","$APN"
Modem Type = Analog Modem

---

### Post by TheFu on 2013-07-18
SMS is a cellular technology, not used on POTS, so sending SMS to non-cellular phones won't work too well.  There are SMS services that work over the internet and many scripts that will interface with those tools. I think google-talk will let you send SMS. Pick whatever SMS service you like and search for the scripting language you prefer ... python, php, perl, ruby, whatever .... and you'll probably find something that will send SMS out.

I wasn't sure about voice use through a modem, so I googled and found this:
[http://superuser.com/questions/230693/how-to-make-phone-calls-using-a-pc-modem-headphone-and-no-actual-phone-instrum](http://superuser.com/questions/230693/how-to-make-phone-calls-using-a-pc-modem-headphone-and-no-actual-phone-instrum)

I do know that a modem can dial any voice number that your POTS phone line can reach, but the person on the other side will hear computer modem screeching unless you tell the modem NOT to try and connect. That is a specific AT command, I suppose. Just hand off the phone line to a voice-capable device ... like a normal $5 phone. For many years, people used computers as a phone dialer, then just picked up the phone and talked after the dialing was complete. The main thing was to have the normal POTS phone off-hook when canceling the modem use.
[http://lists.debian.org/debian-user/2007/08/msg01652.html](http://lists.debian.org/debian-user/2007/08/msg01652.html) seems related.

I hope this helps with your research to a solution.

---

