---
title: "Managing networking service from a watchdog repair binary."
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by herimo on 2009-12-16
Hello,
 
I have an appliance in which I have installed Ubuntu Server 9.04. Requirements for the appliance establish that the network interfaces must be monitored to remain always available (i.e. configured and functional). 
Other requirements exist to monitor applications, memory usage, and other services.
 
I downloaded and installed the watchdog package (watchdog_5.4-10_i386.deb) to help with the system monitoring. I also wrote a script (test_binary) to test the state of elements to be monitored as well as a script (repair_binary) perform any necessary repair if at all possible. The watchdog functionality seems to be working well. For information on the watchdog functionality and configuration options, please refer to ([http://manpages.ubuntu.com/manpages/hardy/man5/watchdog.conf.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/watchdog.conf.5.html)).
 
The only problem I have encountered is related to the networking service. The test_binary is able to detect if any of the configured interfaces (i.e. lo, eth0) is down. It then sends the appropriate notification (error code) to the watchdog. The watchdog in turn calls the repair_binary with the return code it received from the test_binary. 
 
My original version of the repair binary executes the command: 
[COLOR=blue]service networking stop[/COLOR]
[COLOR=blue]service networking start[/COLOR]
The repair binary indicates, via log entries on /var/log/daemon.log and /var/log/syslog, that the interfaces were re-configured correctly. However, the interface eth0 is still not configured.
Then I tried the command [COLOR=blue]service networking restart[/COLOR] to no avail.
 
Interesting enough is the fact that if I run the repair_script manually in the command line as shown below:
 
[COLOR=blue]sudo repair_script.sh 241[/COLOR]
 
all interfaces are reconfigured correctly. The parameter value 241 is the indicator that the network interfaces need to be serviced (restarted). This is implementation specific. 
 
Just for testing purposes, I took the code for the implementation of the restart action within the file /etc/init.d/networking. I copied this code into my repair_binary and it works fine. 
 
However, my concern is that I would have to monitor any future changes to the code in /etc/init.d/networking in order to update my own scripts. 
 
Can anyone provide any ideas for a reason why the interfaces are not getting re-configured?
 
Thank you very much for any help. I really appreciate it.
 
 
P.S. The same scenario is present if I use Ubuntu Desktop as the operating system.

---

