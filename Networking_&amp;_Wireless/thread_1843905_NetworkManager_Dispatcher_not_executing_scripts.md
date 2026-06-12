---
title: "NetworkManager Dispatcher not executing scripts"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by paolora on 2011-09-14
Hello all,

I've a script that depending on network connection changes smtp server in Evolution.

> 

#!/bin/bash

INTERFACCIA="$1"
STATO="$2"
RETE=`iwgetid -s`

if [ "$RETE" == "AndroidAP" ]; then
   NUOVOSMTP="smtp.net.vodafone.it"
fi

SETUPSMTP=`gconftool-2 --get /apps/evolution/mail/accounts | sed "s/\(smtp:\/\/\)[^;]*/\1${NUOVOSMTP}\//g"` 

gconftool-2 --unset /apps/evolution/mail/accounts 

gconftool-2 --type=list --list-type=string --set /apps/evolution/mail/accounts "$SETUPSMTP" 

I've set script permissions according to man instructions and saved the script in folder /etc/NetworkManager/dispatcher.d/ 

If I run the script from shell, everything works fine. If I change network connection, nothing happens.
I've tried to put a sleep "3s" at the beginning, I've also included the complete path of each command, with no result...

What am I missing? :confused:

Thanks!

-Paolo

---

