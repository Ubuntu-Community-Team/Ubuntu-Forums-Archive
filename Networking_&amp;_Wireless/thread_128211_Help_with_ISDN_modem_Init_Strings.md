---
title: "Help with ISDN modem Init Strings"
date: 2006-02-10
forum: Networking &amp; Wireless
---

### Post by Syphin on 2006-02-10
Ok,
 I have a '3Com U.S. Robots ISDN Pro TA-U (3CP3468A)' ISDN/USB modem for my main connection. It's allways worked perfectly on WinXP when I use it.  Both channels connect and stay connected.

But ever sense I started using Linux, I can never get it to work quite right.
When I use the default init strings in wvdial, i cant get it to connect at all.

When I use the 'AT*PPP=3' it connects mabye 1 time out of 20.. and both lines dont connect most of the time.  And when it doesnt work (most of the time) I get this in the console:

```
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT*PPP=3
OK
--> Modem initialized.
--> Sending: ATDT#######
--> Waiting for carrier.
~[7f]}#@!}!} } }4}%}&hFC'}#}$@#}"}&} } } } a}%~~[7f]}#@!}!}!} }4}%}&hFC'}#}$@#}"}&} } } } ([16]~~[7f]}#@!}!}"} }4}%}&hFC'}#}$@#}"}&} } } } b+~~[7f]}#@!}!}#} }4}%}&hFC'}#}$@#}"}&} } } } +8~~[7f]}#@!}!}$} }4}%}&hFC'}#}$@#}"}&} } } } gX~~[7f]}#@!}!}%} }4}%}&hFC'}#}$@#}"}&} } } } 
```
And it goes on with that for a while, then dissconnects and tries again and again.

And when I use 'AT*VI=0*VO=5*PPP=3S67=0' (suggested by the 3com site, for this modem) as the Init string, I get the exact same stuff in the cosolse as above, accept every time it does connect, it connects both channels, and stays connected.


As of late tonight, I tried a new Init string:
'AT&F1X1&A0*VO=1*X0=1024'

```
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: AT&F1X1&A0*VO=1*X0=1024
OK
--> Modem initialized.
--> Sending: ATDT#######
--> Waiting for carrier.
ATDT#######
CONNECT 64000
--> Carrier detected.  Waiting for prompt.
login:
--> Looks like a login prompt.
--> Sending: xxxxx
xxxxx
Password:
--> Looks like a password prompt.
--> Sending: (password)
PPP session from (xxx.xx.xx.xx) to xxx.xx.xx.xxx beginning....~[7f]}#@!}!}!} }4}"}&} } } } }%}&[1f]fpd}'}"}(}"m[05]~
--> PPP negotiation detected.
--> Starting pppd at Fri Feb 10 21:48:14 2006
--> pid of pppd: 9559
--> Using interface ppp0
--> local  IP address xxx.xx.xx.xxx
--> remote IP address xxx.xx.xx.xx
--> primary   DNS address xxx.xxx.xxx.xx
--> secondary DNS address xxx.xxx.xxx.xx
```

Now, this connects every time. But, It only connects on the first channel, never even tries the second.

I've tried the last one with *PPP=3 at the end, and in replace of X0=1024, but with no luck..  If anyone has any knowledge about Init commands, or this modem, and can help, It would help me out alot, and allow me to use my linux box alot more offen.

Thanks :)

---

