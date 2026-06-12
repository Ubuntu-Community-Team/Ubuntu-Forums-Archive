---
title: "Weird DNS problem"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by ckuecker on 2010-06-26
Hello,

I've lost my web server and email server. Both are running and I haven't changed anything in them (that I know of!).

I have a static IP running into a router setup to forward HTTP port 80 and SMTP port 25 to the server. Everything was working fine this morning.

I added one line to the ckent.org.db file, to attempt to allow external access to a device I am working with.

What I did do is start to setup tinydns to replace my running bind9 installation. Now, attempting to access the web site gives a 403 error, and my email client cannot connect to the server. I never finished the tinydns setup - bind is still running. 

When I run dig on my domain, I get this:

```

ckuecker@ckenterprises:~$ dig ckent.org

; <<>> DiG 9.6.1-P2 <<>> ckent.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47784
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 6, ADDITIONAL: 6

;; QUESTION SECTION:
;ckent.org.            IN    A

;; ANSWER SECTION:
ckent.org.        6827    IN    A    66.245.194.29 << WRONG IP? >>

;; AUTHORITY SECTION:
org.            152953    IN    NS    c0.org.afilias-nst.info.
org.            152953    IN    NS    d0.org.afilias-nst.org.
org.            152953    IN    NS    a0.org.afilias-nst.info.
org.            152953    IN    NS    a2.org.afilias-nst.info.
org.            152953    IN    NS    b0.org.afilias-nst.org.
org.            152953    IN    NS    b2.org.afilias-nst.org.

;; ADDITIONAL SECTION:
b0.org.afilias-nst.org.    133312    IN    A    199.19.54.1
b0.org.afilias-nst.org.    133312    IN    AAAA    2001:500:c::1
b2.org.afilias-nst.org.    133312    IN    A    199.249.120.1
b2.org.afilias-nst.org.    133312    IN    AAAA    2001:500:48::1
c0.org.afilias-nst.info. 133312    IN    A    199.19.53.1
c0.org.afilias-nst.info. 133312    IN    AAAA    2001:500:b::1

;; Query time: 27 msec
;; SERVER: 66.254.195.3#53(66.254.195.3)
;; WHEN: Fri Jun 25 23:26:07 2010
;; MSG SIZE  rcvd: 313


```

My static IP is 66.254.194.29, not 66.245.194.29. I can't find this IP anywhere in my bind .db files, or anywhere else.

Files that might help:

/etc/hosts:

```

127.0.0.1    localhost
# 192.168.0.200    ckenterprises.ckent.org ckenterprises
127.0.1.1    ckenterprises

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

/etc/hosts.allow: - this is for a development system I am working with - 'PDK' below, in the DNS zone file.

```

# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#

in.tftpd : 192.168.0.254

```

/etc/bind/zones/ckent.org.db:

```

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
ckent.org.      IN      SOA     ns1.ckent.org. ckenterprises.ckent.org. (
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
ckent.org.      IN      NS              ns1.ckent.org.
ckent.org.      IN      MX     10       mail.ckent.org.


// Replace the IP address with the right IP addresses.
www              IN      A       66.254.194.29
mail             IN      A       66.254.194.29
ns1              IN      A       66.254.194.29
ckenterprises    IN      A       66.254.194.29
pdk             IN     A     66.254.194.29    ,, New line added

```

/etc/bind/zones/29.194.254.66.in-addr.arpa:

```

//replace example.com with your domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA ns1.ckent.org. ckenterprises.ckent.org. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.ckent.org.
29                   IN    PTR    ckent.org

```

Where is the bad IP coming from? It's the only strange thing I can see, and unless I did a typo somewhere, it is inexplicable to me. Pinging [www.ckent.org](www.ckent.org) works, as does mail.ckent.org. Pinging ckenterprises.ckent.org fails.

Any help would be appreciated. My business is dead in the water until I get this problem unscrewed.

Chuck Kuecker

---

### Post by ckuecker on 2010-06-28
May have found the solution. Network Solutions had their master file pointing to IP address 66.245.194.29. They are fixing it now.

---

