---
title: "LSB style header"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by zkab on 2009-01-03
I have made a fresh installation of 8.10 server edition and want to run a startup script and issued following command but received a warning:

sudo update-rc.d my_start_script defaults

update-rc.d: warning: /etc/init.d/my_start_script missing LSB style header

Adding system startup for /etc/init.d/my_start_script ...
/etc/rc0.d/K20my_start_script -> ../init.d/my_start_script
/etc/rc1.d/K20my_start_script -> ../init.d/my_start_script
/etc/rc6.d/K20my_start_script -> ../init.d/my_start_script
/etc/rc2.d/S20my_start_script -> ../init.d/my_start_script
/etc/rc3.d/S20my_start_script -> ../init.d/my_start_script
/etc/rc4.d/S20my_start_script -> ../init.d/my_start_script
/etc/rc5.d/S20my_start_script -> ../init.d/my_start_script

The script 'my_start_script' is in /etc/init.d and is executable ...
How can I fix this or can I just neglect it

---

### Post by skajoeska on 2009-01-27
I have the same issue while trying to add a script set my network card to 10Mbs full duplex.

---

### Post by wbrown on 2009-02-09
Greetings: 

I found a link to this Debian info for startup scripts.  

[http://wiki.debian.org/LSBInitScripts/](http://wiki.debian.org/LSBInitScripts/)

Adding the below and replacing with the info for my script resolved this for me: 

#!/bin/bash
#
### BEGIN INIT INFO
# Provides:          defaultdaemon
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFO

.... rest of script


HTH
Bill.

---

