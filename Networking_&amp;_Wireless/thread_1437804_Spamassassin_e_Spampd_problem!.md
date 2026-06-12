---
title: "Spamassassin e Spampd problem!"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by cellarosi on 2010-03-24
Hi! :)

I'm trying to configure two machine. The firs one with Postfix(192.168.1.97), and the second one with Spamassassin (192.168.1.96).

I have installed "spampd" demon on Spamassassin machine in order to put it listen on 10025 port.
But when I try to connect with "telnet 192.168.1.96 10025", it gives this error:
[HTML]Trying 192.168.1.96...
Connected to 192.168.1.96.
Escape character is '^]'.
Connection closed by foreign host.[/HTML]

And on syslog server the error is
[HTML]spampd[7586]: WARNING!! Error in process_request eval block: /usr/sbin/spampd: socket connect failure: 111[/HTML]

My spampd config file is the sequent:

[HTML]# Defaults file for spampd, the spam proxy daemon
# (spampd is using spamassassin to scan mails)

# On boolean options, 0 means off/no/false, 1 means on/yes/true

# Wether or not to start spampd (0/1)
STARTSPAMPD=1

# where to put the PID file
PIDFILE=/var/run/spampd.pid

# The IP to listen on
#LISTENHOST=127.0.0.1
LISTENHOST=192.168.1.96
# The port to listen on
LISTENPORT=10025

# The host to forward the connection to
DESTHOST=192.168.1.97

# The port to forward the connection to
DESTPORT=10026

# How many parallel checks can be done in parallel
CHILDREN=3

# user ID to run as
USERID=spampd

# group ID to run as
GRPID=spampd

# Wether or not to tag all messages (0/1)
TAGALL=1

# Wether or not to use auto-whitelisting (0/1)
AUTOWHITELIST=0

# Wether or not to do only local checks
# if this is turned on, no network based checks
# (like DNS-Blacklists) are done. (0/1)
LOCALONLY=1
#LOCALONLY=0

# Wether to prefer INET (network,1) for syslog logging
# instead of UNIX (unix domain socket,0) (0/1)
LOGINET=0

# Any additional parameters you want to pass to spampd
#
# The following sample entry enables use of a config file
# by spampd which can be used to override parameters from
# the system-wide SpamAssassin configuration
#
#ADDOPTS="--config=/etc/spampd.conf"
ADDOPTS="-d"[/HTML]

Any ideas?

Thanks in advance! :)

---

### Post by cellarosi on 2010-03-25
up :)

---

### Post by cellarosi on 2010-03-26
No one? :(

---

