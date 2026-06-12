---
title: "using 2 alternate.conf files for wvdial"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by Hume's doona on 2009-12-12
I have 2 usb e169 3g modems with 2 different companies [both cover different areas geographically] and my simple question is:

if instead of starting wvdial with:
```


sudo wvdial

```
i use:
```


sudo wvdial -c /etc/wvdial3.conf

```
will it use /etc/wvdial3.conf instead of /etc/wvdial.conf?

I can't just try it b/c 3 doesn't cover my area, but i will need to for xmas travel

again, sorry if it's dumb, i searched the forums and wiki [and google], but is that whatt the
[code

-c
[/code]
command does? "use the .conf file /X/XXX"? i think that's right

cheers

---

### Post by emigrant on 2009-12-12
i think you should name each .conf differently and run by that name.

---

### Post by GeorgeVita on 2009-12-13
Hi **Hume's doona**,
you can read some info regarding wvdial using terminal command: **man wvdial**

The mistake is that you are using **-c** instead of **-C**
> -c, --chat Run wvdial as a chat replacement from within  pppd ...
-C, --config=CONFIGFILE Run wvdial with CONFIGFILE as the configuration ...

So the correct is: ```
sudo wvdial -C /etc/wvdial3.conf
```
From my point of view, you must create more paragraphs into one configuration file (ex. /etc/wvdial.conf) and use 'paragraph name' as the specific option you need each time:
sudo wvdial fromHome
sudo wvdial HolidaysNow
etc ...

For reference I am giving you my /etc/wvdial.conf which is used for 3 providers, 2-4 modems, using the syntax: sudo wvdial provider modem
```
[Dialer Defaults]
New PPPD = yes
Dial Command = ATDT
Dial Attempts = 1
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","internet"
Phone = *99***1#
Stupid Mode = 1

[Dialer wind]
Username = web
Password = web
Init3 = AT+CGDCONT=1,"IP","gint.b-online.gr"

[Dialer cosmote]
Init3 = AT+CGDCONT=1,"IP","internet"

[Dialer vodafone]
Init3 = AT+CGDCONT=1,"IP","internet"

[Dialer MF636]
Modem = /dev/ttyUSB2

[Dialer E169]
Modem = /dev/ttyUSB0

[Dialer E170]
Modem = /dev/ttyUSB0

[Dialer E220]
Modem = /dev/ttyUSB0

[Dialer 0]
Modem = /dev/ttyUSB0

[Dialer 1]
Modem = /dev/ttyUSB1

[Dialer 2]
Modem = /dev/ttyUSB2

```

Some valid connecting examples with my /etc/wvdial.conf (as above):
sudo wvdial vodafone E169
sudo wvdial vodafone 2
sudo wvdial

Note: 2nd example uses parameter **2** which set to use /dev/ttyUSB2
3rd example connects using only [Dialer Defaults] parameters.

Regards,
George

---

### Post by Hume's doona on 2009-12-13
Thanks for that George

---

