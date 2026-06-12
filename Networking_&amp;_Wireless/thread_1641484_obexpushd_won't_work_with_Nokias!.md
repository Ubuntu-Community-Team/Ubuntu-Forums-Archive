---
title: "obexpushd won't work with Nokias?!"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by timmikins on 2010-12-09
Ubuntu 10.10 on a Mac Mini. I'm using obexpushd to receive files, because I want to use multiple dongles.

When I send an image from my Google Nexus, it works (and the speed problem with previous Ubuntus seems to have gone away - it's as fast as Windows now :-)).

But when I try a Nokia N95, N80 and 3650 the phone says 'sending failed'.

On Ubuntu:

hcidump gives no output at all
obexpushd says:

OBEX_EV_ACCEPTHINT, OBEX_CMD_CONNECT
0: Connection from “bluetooth/[00:60:57:6E:CD:F7]:9&#8243;
0: OBEX_EV_REQHINT, OBEX_CMD_CONNECT
0: OBEX_EV_REQ, OBEX_CMD_CONNECT
0: Sending response code 0
0: OBEX_EV_REQDONE, OBEX_CMD_CONNECT
0: OBEX_EV_REQHINT, OBEX_CMD_PUT
0.1: OBEX_EV_REQCHECK, OBEX_CMD_PUT
0.1: OBEX_EV_REQDONE, OBEX_CMD_PUT
0.1: OBEX_EV_LINKERR, OBEX_CMD_CONNECT

As another datapoint, when I run an Obex server written in Java and using Bluecove on the same hardware, I can receive an image from any of those phones.  But the Bluetooth performance is terrible.

Can anyone advise, please?  I need this to work with as many phones as possible (doesn't seem to be a problem for Mac OS, and even Windows does better than Ubuntu) and I want the option of multiple receiving dongles. 

Thanks in advance,

Tim

---

### Post by Sombra on 2011-01-03
Install the last version:

[http://packages.debian.org/experimental/obexpushd](http://packages.debian.org/experimental/obexpushd)

It will fix Nokia and Samsung from my testing ;-)

---

