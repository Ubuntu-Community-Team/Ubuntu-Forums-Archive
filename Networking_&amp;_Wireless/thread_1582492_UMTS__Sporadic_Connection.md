---
title: "UMTS:  Sporadic Connection"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by asearle on 2010-09-26
Hi Everyone,

I have an Option GT 3G+ EMEA PCMCIA card connecting over UMTS to a local provider here in Germany (FONIC) and was absolutely "bowled over" when the whole thing worked "plug and play" with Ubuntu.  All I can say is bravo!

However, after my initial euphoria I find that although the connection is stable and fast when connected, getting a connection is rather "sporadic".  I thought that this might be an issue on the side of my provider but under windows I seem to get a connection whenever I need one.  Under Ubunut only about 1 in 10 of my attempts to connect is successful.

Does anyone out there have any idea why this is so?  What log files should I look it to see why I am not getting a connection or why this connection is being refused?

Any tips would be gratefully received because I am sure that once the issues are sorted out, this will be a great asset for my laptop.

Many thanks and all the best,
Alan

---

### Post by alexfish on 2010-09-26
hi

can you post the results of this command from the terminal

Code:

[COLOR=Blue]egrep -v '#|^ *$' /etc/ppp/options[/COLOR]

---

### Post by asearle on 2010-09-28
Here are the settings ...

comp@comp-laptop:~$ egrep -v '#|^ *$' /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

... I hope they can help shed some light on the subject.

As it is, I have been trying to identify a pattern in the problem but cannot seem to find one except for the fact that, after lots of "Non-connections", once I am on-line, re-connect seems to be OK.  Maybe that information helps.

Many thanks for any tips that you can give me.

Regards,
Alan

---

### Post by alexfish on 2010-09-28
hi

there is one option that could be added to the options file

from the terminal enter the following code

Code:

[COLOR=Blue]sudo getdit /etc/ppp/options[/COLOR]

add the following line

[COLOR=Blue]replacedefaultroute[/COLOR]

save and exit

see what happens

Also need more info , 

what dial up method are you using for the connection ,

is system 64bit or 32 and which version of Ubuntu

is usb_modeswitch installed (if not installed ,do not install)

can you post the results of this command from the terminal

Code:

[COLOR=Blue]lspci[/COLOR]


you can monitor your connection from the log file viewer / messages on later versions of ubuntu

or from the terminal

code:

[COLOR=Blue]tail -f /var/log/syslog [/COLOR]

this will monitor the connection in real time ; so use before trying the connection

post the results of a situations of none connection and a successful connection

---

### Post by asearle on 2012-03-10
Hi everyone,

In the end I dumped the pcmcia UMTS adaptor and used a newer USB-dongel (by Huwei, supplied by the telecom provider).

That works fine.

Regards,
Alan

---

