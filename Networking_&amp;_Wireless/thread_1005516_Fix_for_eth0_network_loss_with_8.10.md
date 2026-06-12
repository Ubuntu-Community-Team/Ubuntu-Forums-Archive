---
title: "Fix for eth0 network loss with 8.10"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by dfowensby on 2008-12-08
After cruising the threads here for a fix, I found ideas, but still needed to hack around: if you use a tight firewall, or in my case, a port-scan detector/redirector such as PortSentry, this may do the job.

Enter in /etc/rc.local something similar:

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

/etc/init.d/portsentry stop ##check for the correct stop/start script for your particular app

/etc/init.d/networking start

sleep 10

/etc/init.d/portsentry start

exit 0


Substitute your ufw/guarddog/portsentry or whatever, and see if this does the trick. This was my major roadblock to adopting Intrepid, and just about beat me (I'm NOT a coder or geek type). Hope this helps someone!
Luck - O.

---

