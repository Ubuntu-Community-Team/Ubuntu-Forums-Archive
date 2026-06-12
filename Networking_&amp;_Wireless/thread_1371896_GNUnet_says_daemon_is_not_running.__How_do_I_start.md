---
title: "GNUnet says daemon is not running.  How do I start it?"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by Captain_Glen on 2010-01-03
Hi,

I have just install GNUnet (an anonymous p2p file sharing program).  But when I run it, it says the daemon is not running.

How do I start the daemon?

I have tried running gnunet-setup but I still get the same problem.

Any help would be appreciated.

Thanks,
Glen.

---

### Post by Captain_Glen on 2010-01-03
Ok it looks like the daemon was not installed.  I fixed it with sudo apt-get install gnunet-server but now I have a new problem.

When I try to search for stuff.  It disconnects from the daemon after a few seconds.

---

### Post by zerwas on 2010-01-04
Hi Glen,

please have a look in the log of GNUnet in the directory */var/lib/gnunet*. The log files are named in the schema like *daemon-logs-04.01.2010*. (Note: You need appropriate user rights to view the file)

If the file is empty, try starting gnunetd by hand and have a look if it crashes.

Thanks,
zerwas

---

### Post by Captain_Glen on 2010-01-04
Hmmm... I can't find the logs

```
glen@glen-desktop:~$ sudo su
[sudo] password for glen: 
root@glen-desktop:/home/glen# cd /var/lib/gnunet/
root@glen-desktop:/var/lib/gnunet# ls
data  friends  state.sdb
root@glen-desktop:/var/lib/gnunet# cd data
root@glen-desktop:/var/lib/gnunet/data# ls
credit  fs  hosts  shared
root@glen-desktop:/var/lib/gnunet/data# cd ..
root@glen-desktop:/var/lib/gnunet# cd state.sdb/
root@glen-desktop:/var/lib/gnunet/state.sdb# ls
bootstrap-info  FS-LAST-QUOTA  GNUNET-VERSION
root@glen-desktop:/var/lib/gnunet/state.sdb# 
```

---

### Post by zerwas on 2010-01-05
Hey Glen,

Please try to start the daemon by hand to see if there are errors:
```
sudo gnunetd -c /etc/gnunetd.conf -l -L DEBUG -d -u gnunet
```

---

### Post by Captain_Glen on 2010-01-05
```
glen@glen-desktop:~$ sudo gnunetd -c /etc/gnunetd.conf -l -L DEBUG -d -u gnunet
[sudo] password for glen: 
Jan 06 11:24:16 INFO: Loading service `identity'
Jan 06 11:24:16 ERROR: `bind' failed at tcpserver.c:404 with error: Address already in use
Jan 06 11:24:16 FATAL: `bind' failed for port 2087. Is gnunetd already running?
Jan 06 11:24:16 INFO: Unloading service `module_identity'.
Jan 06 11:24:16 FATAL: Core initialization failed.
glen@glen-desktop:~$ 

```

---

### Post by zerwas on 2010-01-07
Thanks for providing the output!

It seems like gnunetd is already running. Please shut it down by executing
```
sudo /etc/init.d/gnunet stop
sudo killall gnunetd
```
Now try starting it again:
```
sudo gnunetd -l -L DEBUG -d -u gnunet
```
This should give some information on what goes wrong.

---

### Post by Captain_Glen on 2010-01-08
Thanks for helping.

Here is the output:

```
glen@glen-desktop:~$ sudo /etc/init.d/gnunet stop
[sudo] password for glen: 
sudo: /etc/init.d/gnunet: command not found
glen@glen-desktop:~$ sudo killall gnunetd
glen@glen-desktop:~$ sudo gnunetd -l -L DEBUG -d -u gnunet
Jan 08 19:48:01 INFO: Loading service `identity'
Jan 08 19:48:01 INFO: Loading service `transport'
Jan 08 19:48:01 INFO: Loading transports `udp tcp http nat'
Jan 08 19:48:01 INFO: Loading service `upnp'
Jan 08 19:48:01 INFO: Loading service `stats'
Jan 08 19:48:01 INFO: Loaded transport `udp'
Jan 08 19:48:01 INFO: Loaded transport `tcp'
Jan 08 19:48:01 INFO: Loaded transport `http'
Jan 08 19:48:01 INFO: Loaded transport `nat'
Jan 08 19:48:01 INFO: I am peer `RAN81EG7IFMTEJGIIAJODA5286K53AJEDD06514VK7IDAKQAAT3N98LIEMONVKU4UQKRI6PT7THCUALLF2C8CA9DG8PAN6OQVT84ISO'.
Jan 08 19:48:01 DEBUG: connection goal is 13 peers (3000000 BPM bandwidth downstream)
Jan 08 19:48:01 INFO: Loading service `session'
Jan 08 19:48:01 INFO: Loading service `pingpong'
Jan 08 19:48:01 DEBUG: `pingpong' registering handlers 2 3 (plaintext and ciphertext)
Jan 08 19:48:01 INFO: Loading service `topology_default'
Jan 08 19:48:01 INFO: `session' registering handler 1 (plaintext and ciphertext)
Jan 08 19:48:01 INFO: Loading service `fragmentation'
Jan 08 19:48:01 INFO: `fragmentation' registering handler 5
Jan 08 19:48:01 INFO: Loading application `advertising'
Jan 08 19:48:01 DEBUG: `advertising' registering handler 0 (plaintext and ciphertext)
Jan 08 19:48:01 INFO: Loading service `state'
Jan 08 19:48:01 INFO: Loading service `bootstrap'
Jan 08 19:48:01 INFO: Loading application `getoption'
Jan 08 19:48:01 INFO: `getoption' registering client handler 2
Jan 08 19:48:01 INFO: Loading application `fs'
Jan 08 19:48:01 INFO: Loading service `datastore'
Jan 08 19:48:01 INFO: Loading service `sqstore_sqlite'
Jan 08 19:48:01 INFO: Loading service `traffic'
Jan 08 19:48:01 INFO: Loading service `dht'
Jan 08 19:48:01 ERROR: `lt_dlopenext' failed for library `libgnunetmodule_dstore' with error: file not found
Jan 08 19:48:01 FATAL: Internal error: assertion failed at service.c:104.
Jan 08 19:48:01 WARNING: Failed to load service `dht'
Jan 08 19:48:01 DEBUG: `fs' registering client handlers 8 9 10 11 12 13 14 15 and P2P handlers 8 9
Jan 08 19:48:01 INFO: Loading application `stats'
Jan 08 19:48:01 INFO: `stats' registering client handlers 32 36 39 and p2p handler 6
Jan 08 19:48:01 INFO: Loading application `traffic'
Jan 08 19:48:01 DEBUG: HTTP uses IPv4 address 192.168.0.4.
Jan 08 19:48:01 DEBUG: UDP uses IPv4 address 192.168.0.4.
Jan 08 19:48:01 INFO: `gnunetd' startup complete.
Jan 08 19:48:01 DEBUG: TCP uses IPv4 address 192.168.0.4.
Jan 08 19:48:01 INFO: upnp: NAT Returned IP: 210.9.139.32

```

---

### Post by zerwas on 2010-01-08
Looks like we're getting closer to the real cause!

Please have a look into your daemon configuration:
```
gksudo gedit /etc/gnunetd.conf
```
Now check that there is an entry
> dstore = dstore_sqlite
in the [MODULES] section.

---

### Post by unclesamslair on 2010-03-19
```
Mar 19 20:58:05 INFO: Loading service `identity'
Mar 19 20:58:05 INFO: Loading service `transport'
Mar 19 20:58:05 INFO: Loading transports `udp tcp http nat'
Mar 19 20:58:05 INFO: Loading service `upnp'
Mar 19 20:58:05 INFO: Loading service `stats'
Mar 19 20:58:05 INFO: Loaded transport `udp'
Mar 19 20:58:05 INFO: Loaded transport `tcp'
Mar 19 20:58:05 INFO: Loaded transport `http'
Mar 19 20:58:05 INFO: Loaded transport `nat'
Mar 19 20:58:05 INFO: I am peer `OA1GM0CPDQETKFTTCNUVHHB3MACSNTK34TPP5C5NM3CKOLOSIVHU0N7P0N6BPS0HLTFL9789QHNLGPNVV8AA9BV56MO6BR4BS5KNULO'.
Mar 19 20:58:05 DEBUG: connection goal is 13 peers (3000000 BPM bandwidth downstream)
Mar 19 20:58:05 INFO: Loading service `session'
Mar 19 20:58:05 INFO: Loading service `pingpong'
Mar 19 20:58:05 DEBUG: `pingpong' registering handlers 2 3 (plaintext and ciphertext)
Mar 19 20:58:05 INFO: Loading service `topology_default'
Mar 19 20:58:05 INFO: `session' registering handler 1 (plaintext and ciphertext)
Mar 19 20:58:05 INFO: Loading service `fragmentation'
Mar 19 20:58:05 INFO: `fragmentation' registering handler 5
Mar 19 20:58:05 INFO: Loading application `advertising'
Mar 19 20:58:05 DEBUG: `advertising' registering handler 0 (plaintext and ciphertext)
Mar 19 20:58:05 INFO: Loading service `state'
Mar 19 20:58:05 INFO: Loading service `bootstrap'
Mar 19 20:58:05 INFO: Loading application `getoption'
Mar 19 20:58:05 INFO: `getoption' registering client handler 2
Mar 19 20:58:05 INFO: Loading application `fs'
Mar 19 20:58:05 INFO: Loading service `datastore'
Mar 19 20:58:05 INFO: Loading service `sqstore_sqlite'
Mar 19 20:58:05 INFO: Loading service `traffic'
Mar 19 20:58:05 INFO: upnp: NAT Returned IP: 70.119.249.7
Mar 19 20:58:05 INFO: Loading service `dht'
Mar 19 20:58:05 ERROR: `lt_dlopenext' failed for library `libgnunetmodule_dstore' with error: file not found
Mar 19 20:58:05 FATAL: Internal error: assertion failed at service.c:104.
Mar 19 20:58:05 WARNING: Failed to load service `dht'
Mar 19 20:58:05 DEBUG: `fs' registering client handlers 8 9 10 11 12 13 14 15 and P2P handlers 8 9
Mar 19 20:58:05 INFO: Loading application `stats'
Mar 19 20:58:05 INFO: `stats' registering client handlers 32 36 39 and p2p handler 6
Mar 19 20:58:05 INFO: Loading application `traffic'
Mar 19 20:58:05 INFO: `gnunetd' startup complete.
Mar 19 20:58:05 DEBUG: HTTP uses IPv4 address 70.119.249.7.
Mar 19 20:58:05 DEBUG: UDP uses IPv4 address 70.119.249.7.
Mar 19 20:58:05 DEBUG: TCP uses IPv4 address 70.119.249.7.

```

also 

```
[PATHS]
GNUNETD_HOME = /var/lib/gnunet

[PATHS]

[Meta]
ADVANCED = YES
RARE = YES
EXPERIMENTAL = NO

[GNUNETD]
PIDFILE = /var/run/gnunetd/gnunetd.pid
HOSTLISTURL = http://gnunet.org/hostlist.php http://gnunet.mine.nu:8081/hostlist http://de.gnunet.org/cgi-bin/hostlist.cgi http://uk.gnunet.org/hostlist
HTTP-PROXY =
USER = gnunet
TRANSPORTS = udp tcp http nat
APPLICATIONS = advertising getoption fs stats traffic
KEEPLOG = 0
LOGFILE = /var/log/gnunetd/gnunetd.log

[FS]
DIR = /var/lib/gnunet/data/fs
INDEX-DIRECTORY = /var/lib/gnunet/data/shared
QUOTA = 1024
ACTIVEMIGRATION = NO

[NETWORK]
PORT = 2087
TRUSTED = 127.0.0.0/8;
INTERFACE = eth0
IP =

[LOGGING]
USER-LEVEL = WARNING
ADMIN-LEVEL = WARNING

[LOAD]
MAXNETDOWNBPSTOTAL = 50000
MAXNETUPBPSTOTAL = 50000
HARDUPLIMIT = 0
MAXCPULOAD = 100
HARDCPULIMIT = 0
BASICLIMITING = YES
INTERFACES = eth0

[GNUNETD-EXPERIMENTAL]
PADDING = NO

[MODULES]
sqstore = sqstore_sqlite
topology = topology_default

[F2F]
FRIENDS = /var/lib/gnunet/friends

[NAT]
LIMITED = NO

[TCP]
PORT = 2086

[TCP6]
PORT = 2088
BLACKLIST =

[UDP]
PORT = 2086
MTU = 1472
BLACKLIST =

[UDP6]
PORT = 2088
MTU = 1452
BLACKLIST =

[HTTP]
PORT = 1080

[GAP]
TABLESIZE = 65536

[MYSQL]
CONFIG = /etc/my.cnf
DATABASE = gnunet
```

---

### Post by zerwas on 2010-03-20
Hi unclesamslair,

please make sure you add a dstore entry in your daemon configuration file like [i posted before]("http://ubuntuforums.org/showpost.php?p=8630691&postcount=9").

The error message itself looks like the SQLite module cannot be found. How did you install GNUnet? Did you compile it yourself? If so, did you make sure you installed the package libsqlite3-0?

You can simply type in this to solve all dependencies:
```
sudo apt-get build-dep gnunet
sudo apt-get build-dep gnunet-server
sudo apt-get build-dep gnunet-gtk
```

Afterwards, go into the directory of GNUnet source code, do a
```
make clean
```
and try to compile again from beginning. After the configure process you should see information on which database will be activated. SQLite support should be active by then!

---

### Post by zissshh on 2010-08-06
sudo gnunetd -l -L DEBUG -d -u gnunet

gnu net start only with this command ,,,ie,,daemon starts only with this command

---

### Post by harrykar on 2011-06-28
Same problem here. I'm on lucid and have installed Gnunet 0.8.1a + gtk gui from official Ubuntu repo. I had setup trough gtk gui open ports 2086 1080 trough firestarter and publish a file but  non work.

here's no log files like *daemon-logs-04.01.2010*
```

# ls /var/lib/gnunet
data  state.sdb

```i start gnunet server manually in debug mode. Here's the output
```

# sudo gnunetd -c /etc/gnunetd.conf -l -L DEBUG -d -u gnunet
Jun 28 08:41:59 INFO: Loading service `identity'
Jun 28 08:41:59 INFO: Loading service `transport'
Jun 28 08:41:59 INFO: Loading transports `udp tcp http nat'
Jun 28 08:41:59 INFO: Loading service `upnp'
Jun 28 08:41:59 INFO: Loading service `stats'
Jun 28 08:41:59 INFO: Loaded transport `udp'
Jun 28 08:41:59 INFO: Loaded transport `tcp'
Jun 28 08:41:59 INFO: Loaded transport `http'
Jun 28 08:41:59 INFO: Loaded transport `nat'
Jun 28 08:41:59 INFO: I am peer `T3LIPHHAOI35GSGFV7219CTUR7QO8C0EB6CNVMSJDRP44MQV339MTQJ7MS9K495AQD39VD054HHP0M5H39KTA548AMTAFUVO32IE3FG'.
Jun 28 08:41:59 DEBUG: connection goal is 138 peers (30000000 BPM bandwidth downstream)
Jun 28 08:41:59 INFO: Loading service `session'
Jun 28 08:41:59 INFO: Loading service `pingpong'
Jun 28 08:41:59 DEBUG: `pingpong' registering handlers 2 3 (plaintext and ciphertext)
Jun 28 08:41:59 INFO: Loading service `topology_default'
Jun 28 08:41:59 INFO: `session' registering handler 1 (plaintext and ciphertext)
Jun 28 08:41:59 INFO: Loading service `fragmentation'
Jun 28 08:41:59 INFO: `fragmentation' registering handler 5
Jun 28 08:41:59 INFO: Loading application `advertising'
Jun 28 08:41:59 DEBUG: `advertising' registering handler 0 (plaintext and ciphertext)
Jun 28 08:41:59 INFO: Loading service `state'
Jun 28 08:41:59 INFO: Loading service `bootstrap'
Jun 28 08:41:59 INFO: Loading application `getoption'
Jun 28 08:41:59 INFO: `getoption' registering client handler 2
Jun 28 08:41:59 INFO: Loading application `fs'
Jun 28 08:41:59 INFO: Loading service `datastore'
Jun 28 08:41:59 INFO: Loading service `sqstore_sqlite'
Jun 28 08:41:59 INFO: Loading service `dv'
Jun 28 08:41:59 INFO: dv: `T3LI' registering P2P handlers 76 75
Jun 28 08:41:59 INFO: Loading service `traffic'
Jun 28 08:41:59 INFO: Loading service `dv_dht'
Jun 28 08:41:59 INFO: core_slots_count returns 138, using 512 buckets for DHT
Jun 28 08:41:59 INFO: Loading service `dstore_sqlite'
Jun 28 08:41:59 INFO: `dv_dht' registering p2p handlers: 20 21 22
Jun 28 08:41:59 DEBUG: `dv_dht' logging disabled
Jun 28 08:41:59 DEBUG: `fs' registering client handlers 8 9 10 11 12 13 14 15 and P2P handlers 8 9
Jun 28 08:41:59 INFO: Loading application `stats'
Jun 28 08:41:59 INFO: `stats' registering client handlers 32 36 39 and p2p handler 6
Jun 28 08:41:59 INFO: Loading application `traffic'
Jun 28 08:41:59 INFO: `gnunetd' startup complete.
Jun 28 08:41:59 DEBUG: HTTP uses IPv4 address 192.168.1.1.
Jun 28 08:41:59 DEBUG: UDP uses IPv4 address 192.168.1.1.
Jun 28 08:41:59 DEBUG: TCP uses IPv4 address 192.168.1.1.
Jun 28 08:42:14 WARNING: Announcing ourselves pointless: no other peers are known to us so far.
Jun 28 08:44:01 WARNING: Message `Announcing ourselves pointless: no other peers are known to us so far.' repeated 1 times in the last 107s
Jun 28 08:44:01 INFO: Bootstrapping using `http://uk.gnunet.org/hostlist'.
Jun 28 08:44:01 INFO: Trying to download hostlist from `http://uk.gnunet.org/hostlist?p=448'
Jun 28 08:44:01 INFO: Downloaded 0 bytes from `http://uk.gnunet.org/hostlist?p=448'.
Jun 28 08:44:14 WARNING: Announcing ourselves pointless: no other peers are known to us so far.
Jun 28 08:48:01 WARNING: Message `Announcing ourselves pointless: no other peers are known to us so far.' repeated 8 times in the last 227s
Jun 28 08:48:01 INFO: Bootstrapping using `http://uk.gnunet.org/hostlist'.
Jun 28 08:48:01 INFO: Trying to download hostlist from `http://uk.gnunet.org/hostlist?p=448'
Jun 28 08:48:02 INFO: Downloaded 0 bytes from `http://uk.gnunet.org/hostlist?p=448'.
Jun 28 08:48:14 WARNING: Announcing ourselves pointless: no other peers are known to us so far.
Jun 28 08:56:02 WARNING: Message `Announcing ourselves pointless: no other peers are known to us so far.' repeated 8 times in the last 468s
Jun 28 08:56:02 INFO: Bootstrapping using `http://uk.gnunet.org/hostlist'.
Jun 28 08:56:02 INFO: Trying to download hostlist from `http://uk.gnunet.org/hostlist?p=448'
Jun 28 08:56:02 INFO: Downloaded 0 bytes from `http://uk.gnunet.org/hostlist?p=448'.
Jun 28 08:56:14 WARNING: Announcing ourselves pointless: no other peers are known to us so far.
Jun 28 09:12:03 WARNING: Message `Announcing ourselves pointless: no other peers are known to us so far.' repeated 17 times in the last 948s
Jun 28 09:12:03 INFO: Bootstrapping using `http://uk.gnunet.org/hostlist'.
Jun 28 09:12:03 INFO: Trying to download hostlist from `http://uk.gnunet.org/hostlist?p=448'
Jun 28 09:12:03 INFO: Downloaded 0 bytes from `http://uk.gnunet.org/hostlist?p=448'.
Jun 28 09:12:14 WARNING: Announcing ourselves pointless: no other peers are known to us so far.

```Seems not find the initial peer list
```

Jun 28 08:44:01 INFO: Downloaded 0 bytes from `http://uk.gnunet.org/hostlist?p=448'.

```the original list was longer in gnunet.conf
```

HOSTLISTURL = http://gnunet.org/hostlist.php http://gnunet.mine.nu:8081/hostlist http://de.gnunet.org/cgi-bin/hostlist.cgi http://uk.gnunet.org/hostlist

```but as reported in  [https://gnunet.org/node/1244](https://gnunet.org/node/1244) the only one that open a download dialog was [http://uk.gnunet.org/hostlist](http://uk.gnunet.org/hostlist) so i delete all the others. Anyway also that last hostlist seems be empty.:(

where can i get a working hostlist? (If that's really the problem)

PS: 
1. my gnunet.conf is:
```

[PATHS]
GNUNETD_HOME = /var/lib/gnunet

[Meta]
ADVANCED = YES
RARE = YES
EXPERIMENTAL = NO

[GNUNETD]
PIDFILE = /var/run/gnunetd/gnunetd.pid
HOSTLISTURL = http://uk.gnunet.org/hostlist
HTTP-PROXY = 
USER = gnunet
TRANSPORTS = udp tcp http nat
APPLICATIONS = advertising getoption fs stats traffic
KEEPLOG = 0
LOGFILE = /var/log/gnunetd/gnunetd.log
HOSTS = $GNUNETD_HOME/data/hosts/
FDLIMIT = 1024
DISABLE-IPV6 = YES
GROUP = gnunet
AUTOSTART = YES
HELLOEXPIRES = 1440
PRIVATE-NETWORK = NO
LIMIT-ALLOW = 
LIMIT-DENY = 

[FS]
DIR = /var/lib/gnunet/data/fs
INDEX-DIRECTORY = /var/lib/gnunet/data/shared
QUOTA = 4096
ACTIVEMIGRATION = NO

[NETWORK]
PORT = 2087
TRUSTED = 127.0.0.0/8;
INTERFACE = eth1
IP = harrykar.dyndns.org
DISABLE-ADVERTISEMENTS = NO
HELLOEXCHANGE = YES
DISABLE-AUTOCONNECT = NO

[LOGGING]
USER-LEVEL = WARNING
ADMIN-LEVEL = WARNING
DEVELOPER = NO

[LOAD]
MAXNETDOWNBPSTOTAL = 500000
MAXNETUPBPSTOTAL = 40000
HARDUPLIMIT = 0
MAXCPULOAD = 100
HARDCPULIMIT = 0
BASICLIMITING = YES
INTERFACES = eth1
PRIORITY = IDLE
MAXIOLOAD = 50

[GNUNETD-EXPERIMENTAL]
PADDING = NO

[MODULES]
sqstore = sqstore_sqlite
topology = topology_default
dstore = dstore_sqlite

[F2F]
FRIENDS = /var/lib/gnunet/friends
FRIENDS-ONLY = NO
MINIMUM = 0

[NAT]
LIMITED = NO

[TCP]
PORT = 2086
UPNP = YES
BLACKLISTV4 = 127.0.0.1;
WHITELISTV4 = 
BLACKLISTV6 = 
WHITELISTV6 = 

[TCP6]
PORT = 2088
BLACKLIST = 

[UDP]
PORT = 2086
MTU = 1472
BLACKLIST = 
UPNP = YES
BLACKLISTV4 = 127.0.0.1;
WHITELISTV4 = 
BLACKLISTV6 = 

[UDP6]
PORT = 2088
MTU = 1452
BLACKLIST = 
WHITELISTV6 = 

[HTTP]
PORT = 1080
ADVERTISED-PORT = 80
UPNP = YES

[GAP]
TABLESIZE = 65536

[MYSQL]
CONFIG = /etc/my.cnf
DATABASE = gnunet

[HOSTLIST]
PORT = 8080

[TCPSERVER]
DISABLE = NO

[SMTP]
EMAIL = gnunet@localhost
RATELIMIT = 0
FILTER = X-mailer: GNUnet
PIPE = $GNUNETD_HOME/smtp-pipe
SERVER = localhost:25
MTU = 65528

[DHT]
TABLESIZE = 1024

[DSTORE]
QUOTA = 1

```2. Probably that's unrelated: I notice that i haven't installed sqlite3(but i have libsqlite3)
TIA

---

### Post by wurm on 2011-08-25
You might try those:
HOSTLISTURL = [http://vserver1236.vserver-on.de/hostlist-074](http://vserver1236.vserver-on.de/hostlist-074)  [http://vserver1236.vserver-on.de/hostlist-074](http://vserver1236.vserver-on.de/hostlist-074) [http://mosquito.dyndns.tv/gnunet-hostlist/hostlist](http://mosquito.dyndns.tv/gnunet-hostlist/hostlist)

I am quite sure i also had to 
```
adduser user_name gnunet
```
else i would be "disconnected" after a short while.

---

### Post by harrykar on 2011-08-27
> **wurm said:**
> You might try those:
HOSTLISTURL = [http://vserver1236.vserver-on.de/hostlist-074](http://vserver1236.vserver-on.de/hostlist-074)  [http://vserver1236.vserver-on.de/hostlist-074](http://vserver1236.vserver-on.de/hostlist-074) [http://mosquito.dyndns.tv/gnunet-hostlist/hostlist](http://mosquito.dyndns.tv/gnunet-hostlist/hostlist)

I am quite sure i also had to 
```
adduser user_name gnunet
```else i would be "disconnected" after a short while.

Thanks for your interest. Meantime [i build from their svn and install]("http://forum.ubuntu-it.org/index.php/topic,473202.0.html") the 0.9pre3 release(no backwards compatible) because the 0.8 is no more supported AFAIK from freenode's #gnunet. Actually 0.9 rel is under development but work fine just after install and open 2086 port either in Ubuntu(if the user has put a firewall) and in router firewall :-). Miss people to use it IMHO

---

### Post by matthewh3 on 2012-01-15
When I run GNUnet Secured P2P package I get the error message in the logs -


Jan 15 21:49:08: Error connecting to localhost:2087. Is the daemon running?


When I run 

sudo gnunetd -l -L DEBUG -d -u gnunet

I get


Jan 15 21:49:22 INFO: Loading service `identity'
Jan 15 21:49:22 INFO: Loading service `transport'
Jan 15 21:49:22 INFO: Loading transports `udp tcp http nat'
Jan 15 21:49:22 INFO: Loading service `upnp'
Jan 15 21:49:22 INFO: Loading service `stats'
Jan 15 21:49:22 INFO: Loaded transport `udp'
Jan 15 21:49:22 INFO: Loaded transport `tcp'
Jan 15 21:49:22 INFO: Loaded transport `http'
Jan 15 21:49:22 INFO: Loaded transport `nat'
Jan 15 21:49:22 INFO: I am peer `LQ2SB6FNOHMLFR6GVS7SAISVJ956DKQAA14OSNPN4PRKQSVCASKNQ0BN0UN977JLHT5G41UM5AFTN5LOBV1TSR5IVB5UGF99JHRBM00'.
Jan 15 21:49:22 DEBUG: connection goal is 256 peers (60000000 BPM bandwidth downstream)
Jan 15 21:49:22 INFO: Loading service `session'
Jan 15 21:49:22 INFO: Loading service `pingpong'
Jan 15 21:49:22 DEBUG: `pingpong' registering handlers 2 3 (plaintext and ciphertext)
Jan 15 21:49:22 INFO: Loading service `topology_default'
Jan 15 21:49:22 INFO: `session' registering handler 1 (plaintext and ciphertext)
Jan 15 21:49:22 INFO: Loading service `fragmentation'
Jan 15 21:49:22 INFO: `fragmentation' registering handler 5
Jan 15 21:49:22 INFO: Loading application `advertising'
Jan 15 21:49:22 DEBUG: `advertising' registering handler 0 (plaintext and ciphertext)
Jan 15 21:49:22 INFO: Loading service `state'
Jan 15 21:49:22 INFO: Loading service `bootstrap'
Jan 15 21:49:22 INFO: Loading application `getoption'
Jan 15 21:49:22 INFO: `getoption' registering client handler 2
Jan 15 21:49:22 INFO: Loading application `fs'
Jan 15 21:49:22 INFO: Loading service `datastore'
Jan 15 21:49:22 INFO: Loading service `sqstore_sqlite'
Jan 15 21:49:22 INFO: Loading service `dv'
Jan 15 21:49:22 INFO: dv: `LQ2S' registering P2P handlers 76 75
Jan 15 21:49:22 INFO: Loading service `traffic'
Jan 15 21:49:22 INFO: Loading service `dv_dht'
Jan 15 21:49:22 INFO: core_slots_count returns 256, using 512 buckets for DHT
Jan 15 21:49:22 INFO: Loading service `dstore_sqlite'
Jan 15 21:49:22 INFO: `dv_dht' registering p2p handlers: 20 21 22
Jan 15 21:49:22 DEBUG: `dv_dht' logging disabled
Jan 15 21:49:22 DEBUG: `fs' registering client handlers 8 9 10 11 12 13 14 15 and P2P handlers 8 9
Jan 15 21:49:22 INFO: Loading application `stats'
Jan 15 21:49:22 INFO: `stats' registering client handlers 32 36 39 and p2p handler 6
Jan 15 21:49:22 INFO: Loading application `traffic'
Jan 15 21:49:22 INFO: `gnunetd' startup complete.
Jan 15 21:49:22 DEBUG: HTTP uses IPv4 address 86.151.41.144.
Jan 15 21:49:22 DEBUG: UDP uses IPv4 address 86.151.41.144.
Jan 15 21:49:22 DEBUG: TCP uses IPv4 address 86.151.41.144.
Jan 15 21:49:37 WARNING: Announcing ourselves pointless: no other peers are known to us so far.
Jan 15 21:51:24 WARNING: Message `Announcing ourselves pointless: no other peers are known to us so far.' repeated 3 times in the last 107s
Jan 15 21:51:24 INFO: Bootstrapping using `[http://gnunet.org/hostlist.php](http://gnunet.org/hostlist.php) [http://gnunet.mine.nu:8081/hostlist](http://gnunet.mine.nu:8081/hostlist) [http://vserver1236.vserver-on.de/hostlist-074](http://vserver1236.vserver-on.de/hostlist-074) [http://mosquito.dyndns.tv/gnunet-hostlist/hostlist](http://mosquito.dyndns.tv/gnunet-hostlist/hostlist)'.
Jan 15 21:51:24 INFO: Trying to download hostlist from `[http://gnunet.org/hostlist.php](http://gnunet.org/hostlist.php) [http://gnunet.mine.nu:8081/hostlist](http://gnunet.mine.nu:8081/hostlist) [http://vserver1236.vserver-on.de/hostlist-074](http://vserver1236.vserver-on.de/hostlist-074) [http://mosquito.dyndns.tv/gnunet-hostlist/hostlist?p=448](http://mosquito.dyndns.tv/gnunet-hostlist/hostlist?p=448)'
Jan 15 21:51:25 ERROR: curl_multi_perform failed at http.c:336: `HTTP response code said error'
Jan 15 21:51:25 INFO: Downloaded 0 bytes from `[http://gnunet.org/hostlist.php](http://gnunet.org/hostlist.php) [http://gnunet.mine.nu:8081/hostlist](http://gnunet.mine.nu:8081/hostlist) [http://vserver1236.vserver-on.de/hostlist-074](http://vserver1236.vserver-on.de/hostlist-074) [http://mosquito.dyndns.tv/gnunet-hostlist/hostlist?p=448](http://mosquito.dyndns.tv/gnunet-hostlist/hostlist?p=448)'.
Jan 15 21:51:37 WARNING: Announcing ourselves pointless: no other peers are known to us so far.
Jan 15 21:55:25 WARNING: Message `Announcing ourselves pointless: no other peers are known to us so far.' repeated 1 times in the last 227s
Jan 15 21:55:25 INFO: Bootstrapping using `[http://gnunet.org/hostlist.php](http://gnunet.org/hostlist.php)'.
Jan 15 21:55:25 INFO: Trying to download hostlist from `[http://gnunet.org/hostlist.php?p=448](http://gnunet.org/hostlist.php?p=448)'
Jan 15 21:55:26 ERROR: curl_multi_perform failed at http.c:336: `HTTP response code said error'
Jan 15 21:55:26 INFO: Downloaded 0 bytes from `[http://gnunet.org/hostlist.php?p=448](http://gnunet.org/hostlist.php?p=448)'.
Jan 15 21:55:37 WARNING: Announcing ourselves pointless: no other peers are known to us so far.

Any help?

---

### Post by harrykar on 2012-01-16
> **matthewh3 said:**
> When I run GNUnet Secured P2P package I get the error message in the logs -
Jan 15 21:49:08: Error connecting to localhost:2087. Is the daemon running?
When I run 
sudo gnunetd -l -L DEBUG -d -u gnunet


Ok  @matthewh3 as you probably can see in a my earlier post, gnunet 0.8.x is dead and 0.9.1 released. if you did *sudo gnunetd* you have 0.8.1 release (from Ubuntu's repository).  
Go to the first post in [http://forum.ubuntu-it.org/index.php/topic,473202.0/all.html](http://forum.ubuntu-it.org/index.php/topic,473202.0/all.html). There i explain how to build(in it lang so use a translator) or if you have a AMD64 architecture you can download the debs from [http://forum.ubuntu-it.org/index.php/topic,473202.msg3750770.html#msg3750770](http://forum.ubuntu-it.org/index.php/topic,473202.msg3750770.html#msg3750770)

If gnunet is difficult to install right now and you want a F2F software i recommend the pretty easy [http://en.wikipedia.org/wiki/Retroshare](http://en.wikipedia.org/wiki/Retroshare)  meanwhile gnunet's guys do the debs :wink:


PS:
Would be better if before install 0.9.x you uninstall(purge) 0.8.x

---

