---
title: "noip2 &quot;Can't locate configuration file...&quot; - but it's right there!"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by Giggity on 2009-02-17
I'd like to get the No-IP DUC working on my computer, but I can't figure out what to make of this...
```
giggity@rcr-laptop ~ $ sudo noip2 -C
[sudo] password for rob: 

Auto configuration for Linux client of no-ip.com.

Multiple network devices have been detected.

Please select the Internet interface from this list.

By typing the number associated with it.
0    eth0
1    wlan0
0
Please enter the login/email string for no-ip.com  giggity@giggity.com
Please enter the password for user 'giggity@giggity.com'  **********

Only one host [rcr-laptop.no-ip.org] is registered to this account.
It will be used.
Do you wish to run something at successful update?[N] (y/N)  ^M

New configuration file '/usr/local/etc/no-ip2.conf' created.

giggity@rcr-laptop ~ $ ls /usr/local/etc
no-ip2.conf
giggity@rcr-laptop ~ $ noip2
Can't locate configuration file /usr/local/etc/no-ip2.conf. (Try -c). Ending!
```As you can see, the configuration file is right there... anyone else having this problem?  Better yet, anyone know how to fix this?

---

### Post by carvilsi on 2009-02-27
Hi.
I had the same problem like you, i fixed giving to the noip2 the path where is the noip2-configuration file with the option -c.
First I configured (the same way as you), then...
# sudo noip2 -c /var/lib/noip2/noip2.conf

See you.

---

### Post by InF3XioN on 2009-07-04
Well I tried this way and it worked.
First type in the terminal
```
sudo chmod 700 /usr/local/bin/noip2
chown root:root /usr/local/bin/noip2

```
You will notice that "sudo noip2" will now execute the process.

Next, save the following shell script
> #! /bin/sh
# /etc/init.d/noip2.sh

# Supplied by no-ip.com
# Modified for Debian GNU/Linux by Eivind L. Rygge <eivind@rygge.org>
# corrected 1-17-2004 by Alex Docauer <alex@docauer.net>

# . /etc/rc.d/init.d/functions  # uncomment/modify for your killproc

DAEMON=/usr/local/bin/noip2
NAME=noip2

test -x $DAEMON || exit 0

case "$1" in
    start)
    echo -n "Starting dynamic address update: "
    start-stop-daemon --start --exec $DAEMON
    echo "noip2."
    ;;
    stop)
    echo -n "Shutting down dynamic address update:"
    start-stop-daemon --stop --oknodo --retry 30 --exec $DAEMON
    echo "noip2."
    ;;

    restart)
    echo -n "Restarting dynamic address update: "
    start-stop-daemon --stop --oknodo --retry 30 --exec $DAEMON
    start-stop-daemon --start --exec $DAEMON
    echo "noip2."
    ;;

    *)
    echo "Usage: $0 {start|stop|restart}"
    exit 1
esac
exit 0 as "noip2.sh" and copy it in "/etc/init.d" directory.
Finally, type the following
```
sudo update-rc.d noip2.sh defaults 90
```
so that the process will start automatically on startup.

---

### Post by Giggity on 2009-07-13
Nice, it worked.  Once again, the solution was so simple I'm embarrassed. :redface:

What a coincidence you posted the answer only a week before I tried this again!

---

### Post by alek66 on 2012-11-24
Hey, how do I force an update... I want to check on no-ip site that the update really worked.

---

### Post by wildmanne39 on 2012-11-24
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

