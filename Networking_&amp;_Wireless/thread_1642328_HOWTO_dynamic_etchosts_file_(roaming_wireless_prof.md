---
title: "HOWTO: dynamic /etc/hosts file (roaming wireless profile)"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by messelink on 2010-12-10
There may be a better way to do this, but I wasn't able to find it. What this code does is check every time a connection is made to a wireless network and comment or uncomment a line in /etc/hosts. For me it solved the problem of being able to reach a server from home or from work using the same url.

This example checks whether you are connected to wireless network MYEXAMPLE. If you are it removes the "#" from the line in /etc/hosts so that now on this machine myexample.dyndns.org will point to 192.168.1.2. If you aren't connected to MYEXAMPLE it will add a "#" in front of the line, making it a comment, and therefore myexample.dyndns.org will point to whatever DNS resolves to.

First add a line to /etc/hosts
```
#192.168.1.2    myexample.dyndns.org     myexample
```

Then create two files in /etc/network/if-up.d

roaming
```
#!/bin/sh

# Parameter settings
WIF="wlan0"
LOCALESSID="MYEXAMPLE"

# Set locations of utils
READLINK=/bin/readlink
DIRNAME=/usr/bin/dirname
IWCONFIG=/sbin/iwconfig
AWK=/usr/bin/awk
SED=/bin/sed

# Find the absolute path this script is in
SCRIPT="`$READLINK -f $0`"
SCRIPTPATH="`$DIRNAME $SCRIPT`"

ESSID="`$IWCONFIG $WIF | $AWK -f $SCRIPTPATH/getESSID.awk`"

if [ "$ESSID" = "$LOCALESSID" ]
then
	`$SED -i 's/#192\.168\.1\.2/192\.168\.1\.2/g' /etc/hosts`
else
	`$SED -i '/#/!s/192\.168\.1\.2/#192\.168\.1\.2/g' /etc/hosts`
fi
```

and 

getESSID.awk
```
#!/bin/awk -f
BEGIN { FS="\"" }; {print $2;exit}
```

Make sure both files are owned by root:root and that only "roaming" is executable and make a symbolic link to roaming in /etc/network/if-down.d.

If someone has a good idea on how to move the IP address to the parameters part of the script, I'd love to hear it.

---

### Post by edouard.lopez on 2011-10-31
Hi,
Seems good, did you find a better solution ? Plus, in the "else"'s block what the '/#/' at the beginning means ?

---

### Post by messelink on 2011-12-10
The # in the beginning of the # line is there to make sure the script only adds a "#" to a line that doesn't have one already. Otherwise, you could end up with multiple # at the beginning of the line in your hosts file if you connect to multiple times to a network that is not your local network.

This setup is working well for me, so I haven't looked at it at all since I have made it. What would you consider a better solution?

---

