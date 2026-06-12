---
title: "Can't configure my system use a local bind9 server with resolv.conf"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by matubaum on 2011-04-11
Hello everybody,
I just configured a bind9 server, in mi local pc (is not a server). The problem i'm having is that when i edit /etc/resolv.conf. It works properly, but when i reboot, the system cleans my changes in the file.

What i wanted to do with bind9 is to route every domain WHATEVER.localhost to a specific directory of my system. And i did it, but i'm just having this problem with my resolv.conf file.

I'm using ubuntu, with networkmanager and my internet connection configured with dhcp.
Any suggestions?

---

### Post by rngresearch on 2011-06-23
This is a quick fix, and I only tested it with Debian, but it should  work with Ubuntu.   Basically, NetworkManager will emulate some of the behavior of  ifupdown by running the scripts in these two directories after an  interface is brought up or down.  See below if you  use ifup and ifdown instead of NetworkManager.

Save the following script as /etc/network/if-up.d/000resolv-fix and then
# chmod 755 /etc/network/if-up.d/000resolv-fix
# cd /etc/network/if-post-down.d
# ln -s ../if-up.d/000resolv-fix

```
#!/bin/sh -e
# /etc/network/if-{up,post-down}.d/000resolv-fix
#     script to re-insert local nameserver at top of
#     /etc/resolv.conf after NetworkManager,
#     or anything else, obliterates it

MYLINE="nameserver 127.0.0.1"

# if /etc/resolv.conf doesn't exist, make it
if ! [ -e /etc/resolv.conf ]; then
    echo "$MYLINE" >/etc/resolv.conf || exit 0
fi

# if $MYLINE is not the top line, edit file
first_line=$(head -n 1 /etc/resolv.conf) || exit 0
if [ "$first_line" != "$MYLINE" ]; then
    echo "$MYLINE" >/etc/resolv.fix || exit 0
    cat /etc/resolv.conf \
        | {
        while read line; do
            if ! echo "$line" | grep -q "$MYLINE"; then
                echo "$line" >>/etc/resolv.fix || exit 0
            fi
        done
    }
    mv -f /etc/resolv.fix /etc/resolv.conf || exit 0
fi

```Note that the files in these directories must be executable (hence the chmod 755).  In case you want to use a different name, also note that scripts are executed in "run-parts" order and only those with run-parts compliant names will be executed.

A final note:  While the above works fine with NetworkManager, there is a problem with ifupdown if ppp gets involved.  Specifically, the script is run *after* the ethernet interface comes up (e.g., eth0).  If using dhcp on a direct ethernet connection, this works fine.  On the other hand, if using pppoe, this script is already finished by the time the ppp connection is negotiated.  This can be worked around by placing more links in more scripts directories!  Place links in /etc/ppp/ip-up.d/ and /etc/ppp/ip-down.d/ to the above script.  Use the same name (000resolv-fix) so the script is run after 0000usepeerdns rewrites /etc/resolv.conf.

Good luck!

---

