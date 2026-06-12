---
title: "Automatic IP address update on Windows DNS Server for Linux workstation"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by snake2903 on 2012-12-27
Hi.... in my company we have our own local domain defined, it' like INT.COMPANY.COM.
I installed fresh Linux Mint 14 (Ubuntu 12.10) distribution and i want to add my computer to domain.

This is what i did.

First i install winbind samba krb5-user.

Then i edit /etc/resolvconf/resolv.conf.d/base file so it looks like this:
```

search int.company.com
dc-1.int.company.com 192.168.0.1
dc-2.int.company.com 192.168.0.2
dc-3.int.company.com 192.168.0.3

```Then edited /etc/krb5.conf file so its looks like this:
```

    [logging]
    default = FILE10000:/var/log/krb5lib.log
    [libdefaults]
    ticket_lifetime = 24000
    default_realm = INT.COMPANY.COM
    [realms]
    INT.COMPANY.COM = {
    kdc = dc-1.int.company.com
    kdc = dc-2.int.company.com
    kdc = dc-3.int.company.com
    admin_server = dc-1.int.company.com
    admin_server = dc-2.int.company.com
    admin_server = dc-3.int.company.com
    master_kdc = dc-1.int.company.com
    default_domain =   INT.COMPANY.COM
    }
    [domain_realm]
    .domain.local = INT.COMPANY.COM
    domain.local = INT.COMPANY.COM

```Then edited /etc/samba/smb.conf file:
```

[global]
    workgroup = INT
    realm = INT.COMPANY.COM
    password server = *
    client use spnego = yes
    netbios name = ws-computer_name
    server string = %h server (Samba %v, Ubuntu)
    dns proxy = no
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    security = ADS
    domain master = no
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    template shell = /bin/bash
    template homedir = /home/%D/%U
    winbind enum groups = yes
    winbind enum users = yes
    winbind use default domain = yes
    usershare allow guests = yes
    wins support = no

```and at least i edited /etc/dhcp/dhclient.conf file
```

# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "ws-computer_name";
#send host-name = gethostname();
send fqdn.fqdn "ws-computer_name.int.company.com";
#send fqdn.fqdn = gethostname();
send fqdn.encoded on;
send fqdn.server-update on;
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 172800;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
supersede domain-name-servers 192.168.0.1 192.168.0.2;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers,
    dhcp6.domain-search, dhcp6.fqdn,
    dhcp6.name-servers, dhcp6.sntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```This is how i configure my computer so i can get into domain.
After restart i login with my domain username and password and everything works except...

For example.... my computer got ip address 192.168.0.150
but when i ping ws-computer_name.int.company.com it returns ip address that i have before, when i have windows on machine, 192.168.0.153...
My machine didn't update automatically my ip address on Windows DNS server.

How to solve this problem? 
When my computer get new ip address, so that address get automatic updated on DNS server?

I hope u understand me.

---

