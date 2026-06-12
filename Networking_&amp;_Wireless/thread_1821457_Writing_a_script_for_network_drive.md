---
title: "Writing a script for network drive"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by andy_spoo on 2011-08-09
If anyone knows how to write a basic script, could some kind sole write one that will check to see if a network drive is powered up, please!

1) Ping an ip address (e.g. 192.168.1.30) to check if a network device is available.

2) If ping replies, mount that device into media directory.

3) Make the above script run only when the Ubuntu system has fully started (So network is up and fully working, etc).

Many thanks,

Andy

---

### Post by andy_spoo on 2011-08-09
OK, I've put this together in /etc/rc.local. It works great if run from a terminal (as root), but won't run from rc.local at boot. I know it's being executed because /tmp/buffalo_mount.log contains "Executing Network Device Detect Script From rc.local". Anyone got any ideas?

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ADDRESS=192.168.1.101
DATETIME="$(date)"
LOGFILE="/tmp/buffalo_mount.log"

echo "Executing Network Device Detect Script From rc.local" >> $LOGFILE
    /bin/ping -c 1 -t 1 $ADDRESS > /dev/null 2> /dev/null  # ping and discard output
    if [ $? -eq 0 ]; then  # check the exit code
        echo "$ADDRESS is LIVE  "+$DATETIME >> $LOGFILE # display the output
	# Ping reply was good, so run the mount command.
	/bin/mount -t cifs -o user=guest,uid=1000,iocharset=utf8,codepage=unicode,unicode,_netdev,rw //$ADDRESS/back-in-time/ /media/Buffalo/Acer-laptop-back_in_time
    else
        echo "$ADDRESS is DEAD  "+$DATETIME >> $LOGFILE
fi

exit 0
```

---

### Post by andy_spoo on 2011-08-11
No replys?? Well I sorted this out myself, with a little help from the stack overflow guys, here:-

[http://stackoverflow.com/questions/6995262/bash-script-code-works-from-terminal-but-not-from-rc-local]("http://stackoverflow.com/questions/6995262/bash-script-code-works-from-terminal-but-not-from-rc-local")

---

