---
title: "T38Modem fail creating pseudo tty"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by mstjohn1974 on 2009-10-21
Hello Guys,

I am trying to setup a HylaFax that uses our Cisco Phone System. The Cisco site is already setup. I am trying to add T38Modems with this command:

sudo /usr/local/bin/t38modem -tt -o /var/log/t38modem.log \
--ptty +/dev/ttyT38-1,+/dev/ttyT38-2 \
--route "modem:.*=h323:<dn>@192.168.54.2" --route "h323:.*=modem:<dn>"

and receive this:

T38Modem Version 0.8.4
 by OpenH323 Project on Unix Linux (2.6.28-11-server-i686)

Route O/G calls:
  modem:.*=h323:<dn> --> 192.168.54.2
Can't create modem for +/dev/ttyT38-1
Can't create modem for +/dev/ttyT38-2
Codecs (in preference order):
 Table:
   G.711-uLaw-64k <1>
   G.711-ALaw-64k <2>
   T.38-UDP <3>
 Set:
   0:
     0:
       G.711-uLaw-64k <1>
       G.711-ALaw-64k <2>
       T.38-UDP <3>

Searching for gatekeeper...

What is the problem with creating the modems?
Can someone help? I am using Ubuntu Server Edition 9.04 and I installed t38modem and openh323 packages from Ubuntu.

Every help is appreciated.

thanks

---

### Post by gyurman on 2010-04-05
These are interest me. Could you solve it?

---

### Post by mstjohn1974 on 2010-04-05
unfortunately not...still looking for a solution

---

### Post by gyurman on 2010-04-06
"Could not open /dev/ptyx0: No such file or directory".

But I probed rebuild kernel with 
CONFIG_UNIX98_PTYS=y
CONFIG_DEVPTS_MULTIPLE_INSTANCES=y
CONFIG_LEGACY_PTYS=y
CONFIG_LEGACY_PTY_COUNT=10
But not working. Why? What can I do for I want send fax? Can anybody any help?

---

