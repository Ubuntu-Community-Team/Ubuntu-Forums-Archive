---
title: "Bind DLZ - named crashing"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by Andruk Tatum on 2013-01-09
I followed the directions [here]("http://ubuntuforums.org/showthread.php?t=823578") for installing Bind with the PostgreSQL DLZ configure option.

I think I have gotten everything working, except named completely crashes whenever I run a command like
```
dig @localhost example.com
```

My /etc/bind/named.conf file looks like:

```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
include "/etc/bind/rndc.key";

//controls {
//          inet * port 953 allow { any; } keys { "rndc-key"; };
//};

logging {
         channel query.log {
                            // Set output log to /var/log/query.log
                            file "/var/log/query.log";
                            // Set severity to dynamic to see all debug messages
                            //severity dynamic;
                            severity debug 9;
         };

         category queries { query.log; };

         channel bind.log {
                           file "/home/andruk/Desktop/bind.log";
                           severity debug 9;
         };

         category general         { bind.log; };
         category database        { bind.log; };
         category security        { bind.log; };
         category config          { bind.log; };
         category resolver        { bind.log; };
         category xfer-in         { bind.log; };
         category xfer-out        { bind.log; };
         category notify          { bind.log; };
         category client          { bind.log; };
         category network         { bind.log; };
         category update          { bind.log; };
         category update-security { bind.log; };
         category dispatch        { bind.log; };
         category dnssec          { bind.log; };
         category lame-servers    { bind.log; };
         category delegation-only { bind.log; };
         category default         { bind.log; };
         category unmatched       { bind.log; };
};

dlz "Postgres Zone" {
                     database "postgres 2
                     {host=127.0.0.1 port=5432 dbname=bind9_dlz user=postgres password=<secret_password>}
                     {SELECT zone FROM dns_record WHERE zone = '$zone$'}
                     {SELECT ttl, type, mx_priority, case when lower(type)='txt' then '\"' || data || '\"' else data end AS data FROM dns_record WHERE zone = '$zone$' AND host = '$record$' AND type <> 'SOA' AND type <> 'NS'}
                     {SELECT ttl, type, data, primary_ns, resp_contact, serial, refresh, retry, expire, minimum FROM dns_record WHERE zone = '$zone$' AND (type = 'SOA' OR type='NS')}
                     {SELECT ttl, type, host, mx_priority, case when lower(type)='txt' then '\"' || data || '\"' else data end AS data, resp_contact, serial, refresh, retry, expire, minimum FROM dns_record WHERE zone = '$zone$' AND type <> 'SOA' AND type <> 'NS'}
                     {SELECT zone FROM dns_xfr WHERE zone = '$zone$' AND client = '$client$'}";
};

```

And the log from my commands (contains bind.log) is
```
andruk@tatum ~/Desktop/binddb $ sudo /etc/init.d/bind9 start 
 * Starting domain name service... bind9                                                                                                [ OK ] 
andruk@tatum ~/Desktop/binddb $ ps aux | grep -v grep | egrep -i 'named|lwresd|rndc' 
bind     18667  0.3  0.6 202912 12992 ?        Ssl  09:27   0:00 /usr/sbin/named -u bind
andruk@tatum ~/Desktop/binddb $ cat -n /var/log/syslog | tail -n +`grep -n "starting BIND" /var/log/syslog | tail -n 1 | sed 's/\([[:digit:]]\+\):.*/\1/'` | grep named 
   813  Jan  9 09:27:09 tatum named[18667]: starting BIND 9.8.1-P1 -u bind
   814  Jan  9 09:27:09 tatum named[18667]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' '--with-dlz-postgres=yes' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2 -DDLZ'
   815  Jan  9 09:27:09 tatum named[18667]: adjusted limit on open files from 4096 to 1048576
   816  Jan  9 09:27:09 tatum named[18667]: found 1 CPU, using 1 worker thread
   817  Jan  9 09:27:09 tatum named[18667]: using up to 4096 sockets
   818  Jan  9 09:27:09 tatum named[18667]: loading configuration from '/etc/bind/named.conf'
   819  Jan  9 09:27:09 tatum named[18667]: reading built-in trusted keys from file '/etc/bind/bind.keys'
   820  Jan  9 09:27:09 tatum named[18667]: using default UDP/IPv4 port range: [1024, 65535]
   821  Jan  9 09:27:09 tatum named[18667]: using default UDP/IPv6 port range: [1024, 65535]
   822  Jan  9 09:27:09 tatum named[18667]: listening on IPv6 interfaces, port 53
   823  Jan  9 09:27:09 tatum named[18667]: listening on IPv4 interface lo, 127.0.0.1#53
   824  Jan  9 09:27:09 tatum named[18667]: listening on IPv4 interface eth0, 192.168.11.48#53
   825  Jan  9 09:27:09 tatum named[18667]: generating session key for dynamic DNS
   826  Jan  9 09:27:09 tatum named[18667]: sizing zone task pool based on 5 zones
   827  Jan  9 09:27:09 tatum named[18667]: Loading 'Postgres Zone' using driver postgres
   828  Jan  9 09:27:09 tatum named[18667]: using built-in root key for view _default
   829  Jan  9 09:27:09 tatum named[18667]: set up managed keys zone for view _default, file 'managed-keys.bind'
   830  Jan  9 09:27:09 tatum named[18667]: Warning: 'empty-zones-enable/disable-empty-zone' not set: disabling RFC 1918 empty zones
   831  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: 254.169.IN-ADDR.ARPA
   832  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
   833  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: 100.51.198.IN-ADDR.ARPA
   834  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
   835  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
   836  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
   837  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
   838  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: D.F.IP6.ARPA
   839  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: 8.E.F.IP6.ARPA
   840  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: 9.E.F.IP6.ARPA
   841  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: A.E.F.IP6.ARPA
   842  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: B.E.F.IP6.ARPA
   843  Jan  9 09:27:09 tatum named[18667]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
   844  Jan  9 09:27:09 tatum named[18667]: command channel listening on 127.0.0.1#953
   845  Jan  9 09:27:09 tatum named[18667]: command channel listening on ::1#953
andruk@tatum ~/Desktop/binddb $ dig @localhost example.com 
; <<>> DiG 9.8.1-P1 <<>> @localhost example.com
; (1 server found)
;; global options: +cmd
;; connection timed out; no servers could be reached
andruk@tatum ~/Desktop/binddb $ cat ~/Desktop/bind.log 
now using logging configuration from config file
load_configuration: success
zone 0.in-addr.arpa/IN: starting load
zone 0.in-addr.arpa/IN: number of nodes in database: 1
no journal file, but that's OK
zone 0.in-addr.arpa/IN: journal rollforward completed successfully: no journal
zone 0.in-addr.arpa/IN: loaded
decrement_reference: delete from rbt: 0x7f10427aff18 0.in-addr.arpa
zone_settimer: zone 0.in-addr.arpa/IN: enter
zone 0.in-addr.arpa/IN: loaded serial 1
zone 127.in-addr.arpa/IN: starting load
zone 127.in-addr.arpa/IN: number of nodes in database: 2
no journal file, but that's OK
zone 127.in-addr.arpa/IN: journal rollforward completed successfully: no journal
zone 127.in-addr.arpa/IN: loaded
decrement_reference: delete from rbt: 0x7f10427aff80 127.in-addr.arpa
zone_settimer: zone 127.in-addr.arpa/IN: enter
zone 127.in-addr.arpa/IN: loaded serial 1
zone 254.169.IN-ADDR.ARPA/IN: starting load
zone 254.169.IN-ADDR.ARPA/IN: number of nodes in database: 0
zone 254.169.IN-ADDR.ARPA/IN: loaded
zone_settimer: zone 254.169.IN-ADDR.ARPA/IN: enter
zone 2.0.192.IN-ADDR.ARPA/IN: starting load
zone 2.0.192.IN-ADDR.ARPA/IN: number of nodes in database: 0
zone 2.0.192.IN-ADDR.ARPA/IN: loaded
zone_settimer: zone 2.0.192.IN-ADDR.ARPA/IN: enter
zone 100.51.198.IN-ADDR.ARPA/IN: starting load
zone 100.51.198.IN-ADDR.ARPA/IN: number of nodes in database: 0
zone 100.51.198.IN-ADDR.ARPA/IN: loaded
zone_settimer: zone 100.51.198.IN-ADDR.ARPA/IN: enter
zone 113.0.203.IN-ADDR.ARPA/IN: starting load
zone 113.0.203.IN-ADDR.ARPA/IN: number of nodes in database: 0
zone 113.0.203.IN-ADDR.ARPA/IN: loaded
zone_settimer: zone 113.0.203.IN-ADDR.ARPA/IN: enter
zone 255.in-addr.arpa/IN: starting load
zone 255.in-addr.arpa/IN: number of nodes in database: 1
no journal file, but that's OK
zone 255.in-addr.arpa/IN: journal rollforward completed successfully: no journal
zone 255.in-addr.arpa/IN: loaded
decrement_reference: delete from rbt: 0x7f103a440010 255.in-addr.arpa
zone_settimer: zone 255.in-addr.arpa/IN: enter
zone 255.in-addr.arpa/IN: loaded serial 1
zone 255.255.255.255.IN-ADDR.ARPA/IN: starting load
zone 255.255.255.255.IN-ADDR.ARPA/IN: number of nodes in database: 0
zone 255.255.255.255.IN-ADDR.ARPA/IN: loaded
zone_settimer: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: starting load
zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: number of nodes in database: 0
zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: loaded
zone_settimer: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: starting load
zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: number of nodes in database: 0
zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: loaded
zone_settimer: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: starting load
zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: number of nodes in database: 0
zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: loaded
zone_settimer: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter
zone D.F.IP6.ARPA/IN: starting load
zone D.F.IP6.ARPA/IN: number of nodes in database: 0
zone D.F.IP6.ARPA/IN: loaded
zone_settimer: zone D.F.IP6.ARPA/IN: enter
zone 8.E.F.IP6.ARPA/IN: starting load
zone 8.E.F.IP6.ARPA/IN: number of nodes in database: 0
zone 8.E.F.IP6.ARPA/IN: loaded
zone_settimer: zone 8.E.F.IP6.ARPA/IN: enter
zone 9.E.F.IP6.ARPA/IN: starting load
zone 9.E.F.IP6.ARPA/IN: number of nodes in database: 0
zone 9.E.F.IP6.ARPA/IN: loaded
zone_settimer: zone 9.E.F.IP6.ARPA/IN: enter
zone A.E.F.IP6.ARPA/IN: starting load
zone A.E.F.IP6.ARPA/IN: number of nodes in database: 0
zone A.E.F.IP6.ARPA/IN: loaded
zone_settimer: zone A.E.F.IP6.ARPA/IN: enter
zone B.E.F.IP6.ARPA/IN: starting load
zone B.E.F.IP6.ARPA/IN: number of nodes in database: 0
zone B.E.F.IP6.ARPA/IN: loaded
zone_settimer: zone B.E.F.IP6.ARPA/IN: enter
zone localhost/IN: starting load
zone localhost/IN: number of nodes in database: 1
no journal file, but that's OK
zone localhost/IN: journal rollforward completed successfully: no journal
zone localhost/IN: loaded
decrement_reference: delete from rbt: 0x7f10427aac10 localhost
zone_settimer: zone localhost/IN: enter
zone localhost/IN: loaded serial 2
managed-keys-zone ./IN: starting load
managed-keys-zone ./IN: number of nodes in database: 1
managed-keys-zone ./IN: journal rollforward completed successfully: up to date
managed-keys-zone ./IN: loaded
managed-keys-zone ./IN: synchronizing trusted keys
set_refreshkeytimer: managed-keys-zone ./IN: enter
managed-keys-zone ./IN: next key refresh: 10-Jan-2013 06:29:33.362
zone_settimer: managed-keys-zone ./IN: enter
decrement_reference: delete from rbt: 0x7f103a428698 .
zone_settimer: managed-keys-zone ./IN: enter
managed-keys-zone ./IN: loaded serial 4
zone authors.bind/CH: starting load
zone authors.bind/CH: number of nodes in database: 0
zone authors.bind/CH: loaded
zone_settimer: zone authors.bind/CH: enter
zone hostname.bind/CH: starting load
zone hostname.bind/CH: number of nodes in database: 0
zone hostname.bind/CH: loaded
zone_settimer: zone hostname.bind/CH: enter
zone version.bind/CH: starting load
zone version.bind/CH: number of nodes in database: 0
zone version.bind/CH: loaded
zone_settimer: zone version.bind/CH: enter
zone id.server/CH: starting load
zone id.server/CH: number of nodes in database: 0
zone id.server/CH: loaded
zone_settimer: zone id.server/CH: enter
dns_zone_maintenance: zone localhost/IN: enter
zone_settimer: zone localhost/IN: enter
dns_zone_maintenance: zone 127.in-addr.arpa/IN: enter
zone_settimer: zone 127.in-addr.arpa/IN: enter
dns_zone_maintenance: zone 0.in-addr.arpa/IN: enter
zone_settimer: zone 0.in-addr.arpa/IN: enter
dns_zone_maintenance: zone 255.in-addr.arpa/IN: enter
zone_settimer: zone 255.in-addr.arpa/IN: enter
dns_zone_maintenance: managed-keys-zone ./IN: enter
zone_settimer: managed-keys-zone ./IN: enter
dns_zone_maintenance: zone 254.169.IN-ADDR.ARPA/IN: enter
zone_settimer: zone 254.169.IN-ADDR.ARPA/IN: enter
dns_zone_maintenance: zone 2.0.192.IN-ADDR.ARPA/IN: enter
zone_settimer: zone 2.0.192.IN-ADDR.ARPA/IN: enter
dns_zone_maintenance: zone 100.51.198.IN-ADDR.ARPA/IN: enter
zone_settimer: zone 100.51.198.IN-ADDR.ARPA/IN: enter
dns_zone_maintenance: zone 113.0.203.IN-ADDR.ARPA/IN: enter
zone_settimer: zone 113.0.203.IN-ADDR.ARPA/IN: enter
dns_zone_maintenance: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
zone_settimer: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
dns_zone_maintenance: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
zone_settimer: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
dns_zone_maintenance: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
zone_settimer: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
dns_zone_maintenance: zone D.F.IP6.ARPA/IN: enter
zone_settimer: zone D.F.IP6.ARPA/IN: enter
dns_zone_maintenance: zone 8.E.F.IP6.ARPA/IN: enter
zone_settimer: zone 8.E.F.IP6.ARPA/IN: enter
dns_zone_maintenance: zone 9.E.F.IP6.ARPA/IN: enter
zone_settimer: zone 9.E.F.IP6.ARPA/IN: enter
dns_zone_maintenance: zone A.E.F.IP6.ARPA/IN: enter
zone_settimer: zone A.E.F.IP6.ARPA/IN: enter
dns_zone_maintenance: zone B.E.F.IP6.ARPA/IN: enter
zone_settimer: zone B.E.F.IP6.ARPA/IN: enter
dns_zone_maintenance: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter
zone_settimer: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter
dns_zone_maintenance: zone version.bind/CH: enter
zone_settimer: zone version.bind/CH: enter
dns_zone_maintenance: zone hostname.bind/CH: enter
zone_settimer: zone hostname.bind/CH: enter
dns_zone_maintenance: zone authors.bind/CH: enter
zone_settimer: zone authors.bind/CH: enter
dns_zone_maintenance: zone id.server/CH: enter
zone_settimer: zone id.server/CH: enter
running
client @0x7f1034097f00: udprecv
client @0x7f10340a60f0: accept
client @0x7f10340b5240: udprecv
client @0x7f10340c3430: accept
client @0x7f10340d1d60: udprecv
client @0x7f10340e00c0: accept
zone_timer: zone 0.in-addr.arpa/IN: enter
zone_maintenance: zone 0.in-addr.arpa/IN: enter
zone_settimer: zone 0.in-addr.arpa/IN: enter
zone_timer: zone 9.E.F.IP6.ARPA/IN: enter
zone_maintenance: zone 9.E.F.IP6.ARPA/IN: enter
zone_settimer: zone 9.E.F.IP6.ARPA/IN: enter
zone_timer: zone 127.in-addr.arpa/IN: enter
zone_maintenance: zone 127.in-addr.arpa/IN: enter
zone_settimer: zone 127.in-addr.arpa/IN: enter
zone_timer: zone 254.169.IN-ADDR.ARPA/IN: enter
zone_maintenance: zone 254.169.IN-ADDR.ARPA/IN: enter
zone_settimer: zone 254.169.IN-ADDR.ARPA/IN: enter
zone_timer: zone 2.0.192.IN-ADDR.ARPA/IN: enter
zone_maintenance: zone 2.0.192.IN-ADDR.ARPA/IN: enter
zone_settimer: zone 2.0.192.IN-ADDR.ARPA/IN: enter
zone_timer: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
zone_maintenance: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
zone_settimer: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
zone_timer: zone 113.0.203.IN-ADDR.ARPA/IN: enter
zone_maintenance: zone 113.0.203.IN-ADDR.ARPA/IN: enter
zone_settimer: zone 113.0.203.IN-ADDR.ARPA/IN: enter
zone_timer: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
zone_maintenance: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
zone_settimer: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
zone_timer: zone 255.in-addr.arpa/IN: enter
zone_maintenance: zone 255.in-addr.arpa/IN: enter
zone_settimer: zone 255.in-addr.arpa/IN: enter
zone_timer: zone D.F.IP6.ARPA/IN: enter
zone_maintenance: zone D.F.IP6.ARPA/IN: enter
zone_settimer: zone D.F.IP6.ARPA/IN: enter
zone_timer: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
zone_maintenance: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
zone_settimer: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
zone_timer: zone version.bind/CH: enter
zone_maintenance: zone version.bind/CH: enter
zone_settimer: zone version.bind/CH: enter
zone_timer: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter
zone_maintenance: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter
zone_settimer: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter
zone_timer: zone localhost/IN: enter
zone_maintenance: zone localhost/IN: enter
zone_settimer: zone localhost/IN: enter
zone_timer: zone A.E.F.IP6.ARPA/IN: enter
zone_maintenance: zone A.E.F.IP6.ARPA/IN: enter
zone_settimer: zone A.E.F.IP6.ARPA/IN: enter
zone_timer: zone authors.bind/CH: enter
zone_maintenance: zone authors.bind/CH: enter
zone_settimer: zone authors.bind/CH: enter
zone_timer: zone hostname.bind/CH: enter
zone_maintenance: zone hostname.bind/CH: enter
zone_settimer: zone hostname.bind/CH: enter
zone_timer: zone id.server/CH: enter
zone_maintenance: zone id.server/CH: enter
zone_settimer: zone id.server/CH: enter
zone_timer: zone 100.51.198.IN-ADDR.ARPA/IN: enter
zone_maintenance: zone 100.51.198.IN-ADDR.ARPA/IN: enter
zone_settimer: zone 100.51.198.IN-ADDR.ARPA/IN: enter
zone_timer: zone 8.E.F.IP6.ARPA/IN: enter
zone_maintenance: zone 8.E.F.IP6.ARPA/IN: enter
zone_settimer: zone 8.E.F.IP6.ARPA/IN: enter
zone_timer: zone B.E.F.IP6.ARPA/IN: enter
zone_maintenance: zone B.E.F.IP6.ARPA/IN: enter
zone_settimer: zone B.E.F.IP6.ARPA/IN: enter
client 127.0.0.1#41673: UDP request
client 127.0.0.1#41673: using view '_default'
client 127.0.0.1#41673: request is not signed
client 127.0.0.1#41673: recursion available
client 127.0.0.1#41673: query

Query String: SELECT zone FROM dns_record WHERE zone = 'example.com'

andruk@tatum ~/Desktop/binddb $ ps aux | grep -v grep | egrep -i 'named|lwresd|rndc' 
andruk@tatum ~/Desktop/binddb $ cat -n /var/log/syslog | tail -n +`grep -n "starting BIND" /var/log/syslog | tail -n 1 | sed 's/\([[:digit:]]\+\):.*/\1/'` | grep named 
   813  Jan  9 09:27:09 khost named[18667]: starting BIND 9.8.1-P1 -u bind
   814  Jan  9 09:27:09 khost named[18667]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' '--with-dlz-postgres=yes' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2 -DDLZ'
   815  Jan  9 09:27:09 khost named[18667]: adjusted limit on open files from 4096 to 1048576
   816  Jan  9 09:27:09 khost named[18667]: found 1 CPU, using 1 worker thread
   817  Jan  9 09:27:09 khost named[18667]: using up to 4096 sockets
   818  Jan  9 09:27:09 khost named[18667]: loading configuration from '/etc/bind/named.conf'
   819  Jan  9 09:27:09 khost named[18667]: reading built-in trusted keys from file '/etc/bind/bind.keys'
   820  Jan  9 09:27:09 khost named[18667]: using default UDP/IPv4 port range: [1024, 65535]
   821  Jan  9 09:27:09 khost named[18667]: using default UDP/IPv6 port range: [1024, 65535]
   822  Jan  9 09:27:09 khost named[18667]: listening on IPv6 interfaces, port 53
   823  Jan  9 09:27:09 khost named[18667]: listening on IPv4 interface lo, 127.0.0.1#53
   824  Jan  9 09:27:09 khost named[18667]: listening on IPv4 interface eth0, 192.168.11.48#53
   825  Jan  9 09:27:09 khost named[18667]: generating session key for dynamic DNS
   826  Jan  9 09:27:09 khost named[18667]: sizing zone task pool based on 5 zones
   827  Jan  9 09:27:09 khost named[18667]: Loading 'Postgres Zone' using driver postgres
   828  Jan  9 09:27:09 khost named[18667]: using built-in root key for view _default
   829  Jan  9 09:27:09 khost named[18667]: set up managed keys zone for view _default, file 'managed-keys.bind'
   830  Jan  9 09:27:09 khost named[18667]: Warning: 'empty-zones-enable/disable-empty-zone' not set: disabling RFC 1918 empty zones
   831  Jan  9 09:27:09 khost named[18667]: automatic empty zone: 254.169.IN-ADDR.ARPA
   832  Jan  9 09:27:09 khost named[18667]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
   833  Jan  9 09:27:09 khost named[18667]: automatic empty zone: 100.51.198.IN-ADDR.ARPA
   834  Jan  9 09:27:09 khost named[18667]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
   835  Jan  9 09:27:09 khost named[18667]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
   836  Jan  9 09:27:09 khost named[18667]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
   837  Jan  9 09:27:09 khost named[18667]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
   838  Jan  9 09:27:09 khost named[18667]: automatic empty zone: D.F.IP6.ARPA
   839  Jan  9 09:27:09 khost named[18667]: automatic empty zone: 8.E.F.IP6.ARPA
   840  Jan  9 09:27:09 khost named[18667]: automatic empty zone: 9.E.F.IP6.ARPA
   841  Jan  9 09:27:09 khost named[18667]: automatic empty zone: A.E.F.IP6.ARPA
   842  Jan  9 09:27:09 khost named[18667]: automatic empty zone: B.E.F.IP6.ARPA
   843  Jan  9 09:27:09 khost named[18667]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
   844  Jan  9 09:27:09 khost named[18667]: command channel listening on 127.0.0.1#953
   845  Jan  9 09:27:09 khost named[18667]: command channel listening on ::1#953
andruk@tatum ~/Desktop/binddb $ 
```

Am I doing anything wrong? Where/how should I begin to troubleshoot from here?

Thanks!

---

### Post by Andruk Tatum on 2013-01-11
I figured it out - I had inserted the data into the wrong database, but the named.conf file was reading from the 'bind9_dlz' database, which contained nothing. The bind9_dlz database had no tables, and I suspect this is why it was erroring out. It is still odd to me that it crashed named though.

Now that I have created the dns_record table and inserted the example.com data from the linked tutorial, the dig command is acting completely normally.

Hope this helps somebody else!

---

