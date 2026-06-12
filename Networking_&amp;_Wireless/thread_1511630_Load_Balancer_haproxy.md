---
title: "Load Balancer haproxy"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by agarwalpranay on 2010-06-17
Hi, I am using haproxy for the first time.I downloaded the latest version 1.4.7 and then unpacked it.then opened the terminal and wrote the command
$make -f Makefile.bsd REGEX=pcre DEBUG= COPTS.generic="-Os -fomit-frame-pointer -mgnu"
 After which an executable haproxy file was created which I copied to /usr/local/sbin.
then i wrote $sudo make install
then I make a configuration file in /etc/haproxy.cfg which is as follows

global
      maxconn 4096
      pidfile /var/run/haproxy.pid
      daemon

defaults
      mode http
      retries 3
      option redispatch
      maxconn 2000
      contimeout 5000
      clitimeout 50000
      srvtimeout 50000

listen GALAXY 192.168.63.51:8080
      mode http
      cookie GALAXY insert
      balance roundrobin
      option httpclose
      option forwardfor
      stats enable
      stats auth myuser:mypass
      server EARTH 192.168.63.52:7634 cookie GALAXY_SERVER_01 check
      server MOON 192.168.63.53 :7634 cookie GALAXY_SERVER_02 check 



But it's not working it is various kind of errors intially it was showing "cannot bind to socket" so tried changing the port number but didn't help
I also used command like $sudo sysctl  net.ipv4.ip_nonlocal_bind=1  But didn't help.
Please Help!!!

---

