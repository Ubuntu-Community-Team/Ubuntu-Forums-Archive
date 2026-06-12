---
title: "Accel-pptpd - no documentation ?"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by Salmus on 2010-11-16
I'm wondering if there is any documentation available for accel-pptp.conf file.

I succesfully compiled accel-pptp without no errors, but I can't get a clue from accel-pptp.conf file ...

[HTML][modules]
#path=/usr/local/lib/accel-pptp
log_file
#log_pgsql
pptp
#pppoe
#l2tp
auth_pap
auth_chap_md5
auth_mschap_v1
auth_mschap_v2
radius
ippool
sigchld
pppd_compat
#shaper_tbf
#chap-secrets

[core]
log-error=/var/log/accel-pptp/core.log
thread-count=4

[ppp]
verbose=1
min-mtu=1000
mtu=1200
mru=1200

[lcp]
echo-interval=30
echo-failure=3

[pptp]
echo-interval=30
verbose=1

[pppoe]
interface=eth0
verbose=1

[l2tp]
#dictionary=/usr/local/share/accel-pptp/l2tp/dictionary
#hello_interval=60
#timeout=60
#rtimeout=5
#retransmit=5
verbose=1

[dns]
#dns1=172.16.0.1
#dns2=172.16.1.1

[radius]
#dictionary=/usr/local/share/accel-pptp/radius/dictionary
nas-identifier=accel-pptp
nas-ip-address=127.0.0.1
gw-ip-address=192.168.100.1
auth_server=127.0.0.1:1812,testing123
acct_server=127.0.0.1:1813,testing123
dm_coa_secret=testing123
verbose=1

[client-ip-range]
10.0.0.0/8

[ip-pool]
gw-ip-address=192.168.0.1
192.168.0.2-255
192.168.1.1-255
192.168.2.1-255
192.168.3.1-255

[log]
log-file=/var/log/accel-pptp/accel-pptp.log
log-emerg=/var/log/accel-pptp/emerg.log
#log-debug=/dev/stdout
copy=1
#color=1
#per-user-dir=per_user
#per-session-dir=per_session
#per-session=1
level=3

[log-pgsql]
conninfo=user=log
log-table=log

[pppd-compat]
#ip-pre-up=/etc/ppp/ip-pre-up
ip-up=/etc/ppp/ip-up
ip-down=/etc/ppp/ip-down
ip-change=/etc/ppp/ip-change
radattr-prefix=/var/run/radattr
verbose=1

[tbf]
#attr=Filter-Id
#burst_factor=0.1
#latency=50
[/HTML]


I currently use pptpd package without any issues, but transfer speed is around 500K/s up or down.

Can anyone give me an example configuration about accel-pptp.conf ? Where I have to set chap-secrets like in pptpd ? From where I define data encryption and so on ... an example of running accel pptpd would be great.


Thanks in advance

---

### Post by Salmus on 2010-11-16
up

---

### Post by xeb on 2010-11-17
> Can anyone give me an example configuration about accel-pptp.conf ?this one you posted ;)

> Where I have to set chap-secrets like in pptpd ?1. build accel-pptp without radius support
2. comment radius in [modules]
3. uncomment chap-secrets in [modules]
4. by default chap-secret file location is /etc/ppp/chap-secrets, you can specify other adding following to accel-pptp.conf:
[chap-secrets]
chap-secrets=/path/to/chap-secrets
5. if chap-secrets also used for ip address assignment you have to specify gw-ip-address in [chap-secrets] as following:
[chap-secrets]
gw-ip-address=192.168.1.1
this address will be used as gateway for vpn clients
6. also if only chap-secrets used for ip address assignment you have to comment ippool in [modules] else move ippool below chap-secrets

> From where I define data encryption and so onmppe is optional by default, so encryptions is depend of client's configuration, there is no way to manually set if mppe is required or forbidden, only via radius at current moment

---

### Post by xeb on 2010-11-17
also please note you can use accel-pptp-0.8x which is based on pptpd

---

### Post by Salmus on 2011-02-21
Well, started using accel pptp 

accel-pptpd v0.8.5  compiled for pppd-2.4.5, linux-2.6.32.27+drm33.12


But:

==> /var/log/daemon.log <==
Feb 21 11:50:58 Core-Node1 pptpd[22127]: MGR: Launching /usr/local/sbin/pptpctrl to handle client
Feb 21 11:50:58 Core-Node1 pptpd[22127]: CTRL: local address = 172.20.0.10
Feb 21 11:50:58 Core-Node1 pptpd[22127]: CTRL: remote address = 192.168.1.1
Feb 21 11:50:58 Core-Node1 pptpd[22127]: CTRL: pppd speed = 115200
Feb 21 11:50:58 Core-Node1 pptpd[22127]: CTRL: pppd options file = /etc/ppp/pptpd-options
Feb 21 11:50:58 Core-Node1 pptpd[22127]: CTRL: Client 92.84.25.31 control connection started
Feb 21 11:50:58 Core-Node1 pptpd[22127]: CTRL: Received PPTP Control Message (type: 1)
Feb 21 11:50:58 Core-Node1 pptpd[22127]: CTRL: Made a START CTRL CONN RPLY packet
Feb 21 11:50:58 Core-Node1 pptpd[22127]: CTRL: I wrote 156 bytes to the client.
Feb 21 11:50:58 Core-Node1 pptpd[22127]: CTRL: Sent packet to client
Feb 21 11:50:58 Core-Node1 pptpd[22127]: CTRL: Received PPTP Control Message (type: 7)
**Feb 21 11:50:58 Core-Node1 pptpd[22127]: CTRL: failed to create PPTP socket (Protocol not supported)**
Feb 21 11:50:58 Core-Node1 pptpd[19884]: MGR: Reaped child 22127



If I start default pptpd deamon, everything works flawlessly, but with accel pptp I get "protocol not supported".

My /etc/pptpd.conf

```
ppp /usr/sbin/pppd
option /etc/ppp/pptpd-options
stimeout 15
speed 115200

localip 172.20.0.10
#remoteip 172.20.0.100-150
debug

```

My /etc/ppp/pptpd-options

```
name pptpd
noauth
refuse-eap
refuse-chap
refuse-mschap
refuse-pap
nobsdcomp
nodeflate
novj
novjccomp
require-mppe-128
require-mschap-v2
mppe required,stateless
debug

```


My /etc/ppp/chap-secrets

```

myuser          pptpd           myplainpassword   172.20.0.90
```


Forgot to mention, I'm running lucid 10.04.2
Any help will be appreciated.
Thanks

---

### Post by Salmus on 2011-02-21
up

---

### Post by Salmus on 2011-02-22
up:(

---

### Post by Salmus on 2011-02-23
last up ...

---

