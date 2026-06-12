---
title: "Can ping but have no web"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by costis on 2013-02-17
Dear ubuntu users,

I'm encountering a peculiar problem.
I can ping anything, but I do not have web access: ```
$ wget www.google.com
--2013-02-18 02:38:11--  http://www.google.com/
Resolving www.google.com (www.google.com)... 173.194.39.244, 173.194.39.240, 173.194.39.242, ...
Connecting to www.google.com (www.google.com)|173.194.39.243|:80... failed: No route to host.
Connecting to www.google.com (www.google.com)|2a00:1450:4017:801::1014|:80... failed: Network is unreachable.

```and I cannot figure out why, since I have not done any change that could spoil the system. I did an upgrade to 12.04.2, but the problem appeared a few hours later.

Could you please help me?


```

$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:2d:a4:c5  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe2d:a4c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:692345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:397918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:591184461 (591.1 MB)  TX bytes:65437324 (65.4 MB)
          Interrupt:4 Base address:0xec00 



$ ping www.google.com
PING www.google.com (173.194.39.241) 56(84) bytes of data.
64 bytes from sof01s02-in-f17.1e100.net (173.194.39.241): icmp_req=1 ttl=59 time=19.7 ms
64 bytes from sof01s02-in-f17.1e100.net (173.194.39.241): icmp_req=2 ttl=59 time=19.1 ms
^C
--- www.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 19.132/19.431/19.730/0.299 ms


$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         dsldevice.lan   0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0


$ dig
; <<>> DiG 9.8.1-P1 <<>>
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 46024
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 15

;; QUESTION SECTION:
;.				IN	NS

;; ANSWER SECTION:
.			246700	IN	NS	d.root-servers.net.
.			246700	IN	NS	j.root-servers.net.
.			246700	IN	NS	a.root-servers.net.
.			246700	IN	NS	l.root-servers.net.
.			246700	IN	NS	k.root-servers.net.
.			246700	IN	NS	c.root-servers.net.
.			246700	IN	NS	i.root-servers.net.
.			246700	IN	NS	h.root-servers.net.
.			246700	IN	NS	b.root-servers.net.
.			246700	IN	NS	g.root-servers.net.
.			246700	IN	NS	e.root-servers.net.
.			246700	IN	NS	f.root-servers.net.
.			246700	IN	NS	m.root-servers.net.

;; ADDITIONAL SECTION:
a.root-servers.net.	505804	IN	A	198.41.0.4
a.root-servers.net.	505812	IN	AAAA	2001:503:ba3e::2:30
b.root-servers.net.	508590	IN	A	192.228.79.201
c.root-servers.net.	508590	IN	A	192.33.4.12
d.root-servers.net.	508589	IN	A	199.7.91.13
d.root-servers.net.	24137	IN	AAAA	2001:500:2d::d
e.root-servers.net.	508589	IN	A	192.203.230.10
f.root-servers.net.	508590	IN	A	192.5.5.241
g.root-servers.net.	508590	IN	A	192.112.36.4
h.root-servers.net.	508590	IN	A	128.63.2.53
i.root-servers.net.	508589	IN	A	192.36.148.17
j.root-servers.net.	508590	IN	A	192.58.128.30
k.root-servers.net.	508590	IN	A	193.0.14.129
l.root-servers.net.	508590	IN	A	199.7.83.42
m.root-servers.net.	505993	IN	A	202.12.27.33

;; Query time: 36 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Feb 18 02:37:10 2013
;; MSG SIZE  rcvd: 492



$ dig www.google.com
; <<>> DiG 9.8.1-P1 <<>> www.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15716
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;www.google.com.			IN	A

;; ANSWER SECTION:
www.google.com.		111	IN	A	173.194.39.241
www.google.com.		111	IN	A	173.194.39.240
www.google.com.		111	IN	A	173.194.39.242
www.google.com.		111	IN	A	173.194.39.244
www.google.com.		111	IN	A	173.194.39.243

;; AUTHORITY SECTION:
google.com.		73910	IN	NS	ns3.google.com.
google.com.		73910	IN	NS	ns4.google.com.
google.com.		73910	IN	NS	ns1.google.com.
google.com.		73910	IN	NS	ns2.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.		74641	IN	A	216.239.32.10
ns2.google.com.		78313	IN	A	216.239.34.10
ns3.google.com.		75826	IN	A	216.239.36.10
ns4.google.com.		75826	IN	A	216.239.38.10

;; Query time: 80 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Feb 18 02:35:23 2013
;; MSG SIZE  rcvd: 248


$  sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

$ uname -a
Linux madrid 3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:57 UTC 2013 i686 athlon i386 GNU/Linux

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


```

---

### Post by Jakssoul on 2013-02-17
I feel like you have a firewall enabled that is not allowing your Web Browser to connect. Would this be accurate?

---

### Post by sanderj on 2013-02-17
Have you already tried a reboot? If that doesn't help: what's the output of:

```

mtr -rc2 8.8.8.8

ssh shell.xs4all.nl



```

---

### Post by costis on 2013-02-18
> **Jakssoul said:**
> I feel like you have a firewall enabled that is not allowing your Web Browser to connect. Would this be accurate?

Dear Jakssoul, 

I have not enabled any firewall on this machine, however its output is:```
$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.3  0.1   3668  2028 ?        Ss   10:43   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    10:43   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    10:43   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    10:43   0:00 [kworker/0:0]
root         5  0.5  0.0      0     0 ?        S    10:43   0:01 [kworker/u:0]
root         6  0.0  0.0      0     0 ?        S    10:43   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    10:43   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S<   10:43   0:00 [cpuset]
root         9  0.0  0.0      0     0 ?        S<   10:43   0:00 [khelper]
root        10  0.0  0.0      0     0 ?        S    10:43   0:00 [kdevtmpfs]
root        11  0.0  0.0      0     0 ?        S<   10:43   0:00 [netns]
root        12  0.0  0.0      0     0 ?        S    10:43   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    10:43   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S<   10:43   0:00 [kintegrityd]
root        15  0.0  0.0      0     0 ?        S<   10:43   0:00 [kblockd]
root        16  0.0  0.0      0     0 ?        S<   10:43   0:00 [ata_sff]
root        17  0.0  0.0      0     0 ?        S    10:43   0:00 [khubd]
root        18  0.0  0.0      0     0 ?        S<   10:43   0:00 [md]
root        19  0.1  0.0      0     0 ?        S    10:43   0:00 [kworker/u:1]
root        20  0.0  0.0      0     0 ?        S    10:43   0:00 [kworker/0:1]
root        21  0.0  0.0      0     0 ?        S    10:43   0:00 [khungtaskd]
root        22  0.0  0.0      0     0 ?        S    10:43   0:00 [kswapd0]
root        23  0.0  0.0      0     0 ?        SN   10:43   0:00 [ksmd]
root        24  0.0  0.0      0     0 ?        SN   10:43   0:00 [khugepaged]
root        25  0.0  0.0      0     0 ?        S    10:43   0:00 [fsnotify_mark]
root        26  0.0  0.0      0     0 ?        S    10:43   0:00 [ecryptfs-kthrea]
root        27  0.0  0.0      0     0 ?        S<   10:43   0:00 [crypto]
root        35  0.0  0.0      0     0 ?        S<   10:43   0:00 [kthrotld]
root        36  0.0  0.0      0     0 ?        S    10:43   0:00 [kworker/u:2]
root        37  0.0  0.0      0     0 ?        S    10:43   0:00 [kworker/0:2]
root        57  0.0  0.0      0     0 ?        S<   10:44   0:00 [devfreq_wq]
root       170  0.0  0.0      0     0 ?        S<   10:44   0:00 [firewire]
root       175  0.0  0.0      0     0 ?        S    10:44   0:00 [scsi_eh_0]
root       176  0.0  0.0      0     0 ?        S    10:44   0:00 [scsi_eh_1]
root       177  0.0  0.0      0     0 ?        S    10:44   0:00 [kworker/u:3]
root       231  0.0  0.0      0     0 ?        S    10:44   0:00 [jbd2/sda2-8]
root       232  0.0  0.0      0     0 ?        S<   10:44   0:00 [ext4-dio-unwrit]
root       306  0.0  0.0   2832   608 ?        S    10:44   0:00 upstart-udev-bridge --daemon
root       312  0.0  0.1   3252  1464 ?        Ss   10:44   0:00 /sbin/udevd --daemon
root       439  0.0  0.1   6680  2252 ?        Ss   10:44   0:00 /usr/sbin/sshd -D
102        454  0.2  0.1   3768  1488 ?        Ss   10:44   0:00 dbus-daemon --system --fork --activation=upstart
root       476  0.0  0.1   4744  1332 ?        Ss   10:44   0:00 /usr/sbin/bluetoothd
syslog     488  0.0  0.1  30036  1512 ?        Sl   10:44   0:00 rsyslogd -c5
avahi      512  0.0  0.1   3568  1644 ?        S    10:44   0:00 avahi-daemon: running [madrid.local]
avahi      514  0.0  0.0   3452   432 ?        S    10:44   0:00 avahi-daemon: chroot helper
root       517  0.0  0.0      0     0 ?        S<   10:44   0:00 [krfcommd]
root       547  0.0  0.2  11072  3416 ?        Ss   10:44   0:00 /usr/sbin/cupsd -F
root       573  0.0  0.0      0     0 ?        S<   10:44   0:00 [kpsmoused]
root       581  0.0  0.0      0     0 ?        S    10:44   0:00 [pccardd]
root       639  0.0  0.0   3248  1040 ?        S    10:44   0:00 /sbin/udevd --daemon
root       644  0.0  0.0   3248  1048 ?        S    10:44   0:00 /sbin/udevd --daemon
root       679  0.0  0.3  21396  4764 ?        Ss   10:44   0:00 smbd -F
root       706  0.0  0.1  21476  1264 ?        S    10:44   0:00 smbd -F
root       720  0.0  0.2   7224  2736 ?        Ss   10:44   0:00 /usr/sbin/modem-manager
root       733  0.0  0.4  31124  4932 ?        Ssl  10:44   0:00 NetworkManager
root       742  0.2  0.3  25360  3728 ?        Sl   10:44   0:00 /usr/lib/policykit-1/polkitd --no-debug
root       748  0.0  0.0   2844   376 ?        S    10:44   0:00 upstart-socket-bridge --daemon
root       852  0.0  0.0   4632   844 tty4     Ss+  10:44   0:00 /sbin/getty -8 38400 tty4
root       860  0.0  0.0   4632   832 tty5     Ss+  10:44   0:00 /sbin/getty -8 38400 tty5
root       878  0.0  0.1   5520  2164 tty2     Ss   10:44   0:00 /bin/login --       
root       879  0.0  0.0   4632   836 tty3     Ss+  10:44   0:00 /sbin/getty -8 38400 tty3
root       886  0.0  0.0   4632   832 tty6     Ss+  10:44   0:00 /sbin/getty -8 38400 tty6
root       914  0.0  0.0   2176   684 ?        Ss   10:44   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       916  0.0  0.0   2620   864 ?        Ss   10:44   0:00 cron
daemon     917  0.0  0.0   2468   344 ?        Ss   10:44   0:00 atd
whoopsie   923  0.0  0.3  25932  4364 ?        Ssl  10:44   0:00 whoopsie
root       930  0.0  0.2  33016  2988 ?        Ssl  10:44   0:00 lightdm
root       964  1.8  5.6 104456 68488 tty7     Ss+  10:44   0:03 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7
root      1007  0.0  0.0      0     0 ?        S    10:44   0:00 [flush-8:0]
root      1033  0.0  0.1   4576  1396 ?        Ss   10:44   0:00 /usr/lib/postfix/master
root      1183  0.0  0.2  18244  3460 ?        Sl   10:44   0:00 lightdm --session-child 16 19
root      1194  0.0  0.2  15836  3200 ?        Sl   10:44   0:00 /usr/lib/accountsservice/accounts-daemon
root      1209  0.0  0.0   4632   840 tty1     Ss+  10:44   0:00 /sbin/getty -8 38400 tty1
root      1223  0.0  0.2  29216  3516 ?        Sl   10:44   0:00 /usr/sbin/console-kit-daemon --no-daemon
lightdm   1297  0.0  0.0   2236   528 ?        Ss   10:44   0:00 /bin/sh /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unit
lightdm   1302  0.0  0.0   3664  1028 ?        Ss   10:44   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --sess
lightdm   1303  0.8  1.3 234096 15908 ?        Sl   10:44   0:01 /usr/sbin/unity-greeter
lightdm   1305  0.0  0.2  42452  3116 ?        Sl   10:44   0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher --launch-immediately
lightdm   1310  0.0  0.1   3256  1348 ?        S    10:44   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf
lightdm   1317  0.0  0.2  17000  2996 ?        Sl   10:44   0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
lightdm   1320  0.0  0.1   8404  2096 ?        S    10:44   0:00 /usr/lib/gvfs/gvfsd
lightdm   1322  0.0  0.2  33736  2548 ?        Sl   10:44   0:00 /usr/lib/gvfs//gvfs-fuse-daemon -f /var/lib/lightdm/.gvfs
lightdm   1329  0.0  0.1  32492  2344 ?        Sl   10:44   0:00 /usr/lib/dconf/dconf-service
lightdm   1335  0.0  0.4  54232  5104 ?        Sl   10:44   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
root      1341  0.0  0.1   8864  2356 ?        S    10:44   0:00 lightdm --session-child 12 19
lightdm   1346  0.0  0.3  74420  4800 ?        Sl   10:44   0:00 /usr/lib/indicator-session/indicator-session-service
lightdm   1351  0.0  0.4  70396  5916 ?        Sl   10:44   0:00 /usr/lib/indicator-datetime/indicator-datetime-service
root      1353  0.0  0.2  28392  3584 ?        Sl   10:44   0:00 /usr/lib/upower/upowerd
lightdm   1355  0.0  0.3 116444  4732 ?        Sl   10:44   0:00 /usr/lib/indicator-sound/indicator-sound-service
lightdm   1387  0.0  0.1   7980  2304 ?        S    10:44   0:00 /usr/lib/geoclue/geoclue-master
lightdm   1395  0.0  0.2   9928  3400 ?        S    10:44   0:00 /usr/lib/i386-linux-gnu/gconf/gconfd-2
lightdm   1404  0.0  0.3  99172  4724 ?        S<l  10:44   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1407  0.0  0.0  21328  1196 ?        SNl  10:44   0:00 /usr/lib/rtkit/rtkit-daemon
lightdm   1431  0.0  0.3  21336  4292 ?        S    10:44   0:00 /usr/lib/ubuntu-geoip/ubuntu-geoip-provider
lightdm   1472  0.0  0.2  14072  2476 ?        S    10:44   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
costis    1614  0.4  0.6  11088  7400 tty2     S+   10:44   0:00 -bash
root      1661  0.0  0.1   2928  1220 ?        S    10:44   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client
nobody    1718  0.0  0.0   5400  1104 ?        S    10:44   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts -
postfix   1764  0.0  0.1   4600  1256 ?        S    10:44   0:00 pickup -l -t fifo -u -c
postfix   1765  0.0  0.1   4648  1280 ?        S    10:44   0:00 qmgr -l -t fifo -u
root      1804  0.0  0.1  13320  1748 ?        Ss   10:44   0:00 nmbd -D
root      1819  0.0  0.2  11872  3584 ?        Ss   10:45   0:00 sshd: costis [priv] 
costis    1917  0.0  0.1  11872  1576 ?        S    10:45   0:00 sshd: costis@pts/0  
costis    1918  0.4  0.6  11080  7392 pts/0    Ss+  10:45   0:00 -bash
root      2019  0.1  0.2  11872  3584 ?        Ss   10:46   0:00 sshd: costis [priv] 
costis    2117  0.0  0.1  11872  1576 ?        S    10:46   0:00 sshd: costis@pts/2  
costis    2118  0.6  0.6  11080  7396 pts/2    Ss   10:46   0:00 -bash
costis    2220  0.0  0.0   4944  1112 pts/2    R+   10:48   0:00 ps aux

```

Also, no firewall is enabled on the ADSL+ modem/router (another machine is connected through it without any problem.

Thanks.

---

### Post by costis on 2013-02-18
> **sanderj said:**
> Have you already tried a reboot? If that doesn't help: what's the output of:
```

mtr -rc2 8.8.8.8
ssh shell.xs4all.nl

```

Dear sanderj,

```
$ mtr -rc2 8.8.8.8
HOST: madrid                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- dsldevice.lan              0.0%     2   64.1  65.1  64.1  66.0   1.3
  2.|-- bbras-llu-lsf-01L500.fort  0.0%     2   15.6  15.7  15.6  15.9   0.2
  3.|-- xe0-0-0.core-lsf-08.forth  0.0%     2   15.3  15.4  15.3  15.6   0.2
  4.|-- 74.125.48.74               0.0%     2   19.8  20.0  19.8  20.1   0.2
  5.|-- 209.85.240.162             0.0%     2   34.8  34.6  34.3  34.8   0.3
  6.|-- 72.14.234.11               0.0%     2   55.4  89.0  55.4 122.6  47.5
  7.|-- 209.85.254.118            50.0%     2   87.6  87.6  87.6  87.6   0.0
  8.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
  9.|-- google-public-dns-a.googl  0.0%     2   53.4  53.4  53.4  53.4   0.0

$ mtr -rc10 8.8.8.8
HOST: madrid                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- dsldevice.lan              0.0%    10   23.2  33.8  23.2  52.1  10.3
  2.|-- bbras-llu-lsf-01L500.fort  0.0%    10   14.5  19.6  14.5  44.0   9.9
  3.|-- xe0-0-0.core-lsf-08.forth  0.0%    10   14.9  19.4  14.9  44.9   9.6
  4.|-- 74.125.48.74               0.0%    10   73.1  34.2  19.2  73.1  21.9
  5.|-- 209.85.240.162             0.0%    10   34.0  37.0  33.9  58.3   7.6
  6.|-- 72.14.234.11               0.0%    10   54.6  57.3  54.0  82.6   8.9
  7.|-- 209.85.254.118             0.0%    10   53.7  58.1  53.7  79.3   8.4
    |  `|-- 209.85.254.112
  8.|-- ???                       100.0    10    0.0   0.0   0.0   0.0   0.0
  9.|-- google-public-dns-a.googl  0.0%    10   54.3  54.6  49.4  65.9   5.9


$ ssh shell.xs4all.nl
ssh: connect to host shell.xs4all.nl port 22: Network is unreachable


$ wget 173.194.39.241
--2013-02-18 11:00:00--  http://8.8.8.8/
Connecting to 8.8.8.8:80... failed: No route to host.

```

Thank you! :)

---

### Post by sanderj on 2013-02-18
On what kind of network are you? Home network, or work, or ... ?

Could it be there is a proxy or firewall?

---

### Post by fdrake on 2013-02-18
can you show us your open ports?
```
netstat --listen localhost
```

---

### Post by rnerwein on 2013-02-18
> **costis said:**
> Dear sanderj,

```
$ mtr -rc2 8.8.8.8
HOST: madrid                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- dsldevice.lan              0.0%     2   64.1  65.1  64.1  66.0   1.3
  2.|-- bbras-llu-lsf-01L500.fort  0.0%     2   15.6  15.7  15.6  15.9   0.2
  3.|-- xe0-0-0.core-lsf-08.forth  0.0%     2   15.3  15.4  15.3  15.6   0.2
  4.|-- 74.125.48.74               0.0%     2   19.8  20.0  19.8  20.1   0.2
  5.|-- 209.85.240.162             0.0%     2   34.8  34.6  34.3  34.8   0.3
  6.|-- 72.14.234.11               0.0%     2   55.4  89.0  55.4 122.6  47.5
  7.|-- 209.85.254.118            50.0%     2   87.6  87.6  87.6  87.6   0.0
  8.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
  9.|-- google-public-dns-a.googl  0.0%     2   53.4  53.4  53.4  53.4   0.0

$ mtr -rc10 8.8.8.8
HOST: madrid                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- dsldevice.lan              0.0%    10   23.2  33.8  23.2  52.1  10.3
  2.|-- bbras-llu-lsf-01L500.fort  0.0%    10   14.5  19.6  14.5  44.0   9.9
  3.|-- xe0-0-0.core-lsf-08.forth  0.0%    10   14.9  19.4  14.9  44.9   9.6
  4.|-- 74.125.48.74               0.0%    10   73.1  34.2  19.2  73.1  21.9
  5.|-- 209.85.240.162             0.0%    10   34.0  37.0  33.9  58.3   7.6
  6.|-- 72.14.234.11               0.0%    10   54.6  57.3  54.0  82.6   8.9
  7.|-- 209.85.254.118             0.0%    10   53.7  58.1  53.7  79.3   8.4
    |  `|-- 209.85.254.112
  8.|-- ???                       100.0    10    0.0   0.0   0.0   0.0   0.0
  9.|-- google-public-dns-a.googl  0.0%    10   54.3  54.6  49.4  65.9   5.9


$ ssh shell.xs4all.nl
ssh: connect to host shell.xs4all.nl port 22: Network is unreachable


$ wget 173.194.39.241
--2013-02-18 11:00:00--  http://8.8.8.8/
Connecting to 8.8.8.8:80... failed: No route to host.

```Thank you! :)
hi
what gives you: nslookup [www.google.com](www.google.com)
if you get an ip-address try in a terminal: e.g.: firefox the_received_ip_address
what's the message you get if it don't work (just timeout ? )
ciao

---

### Post by costis on 2013-02-18
Dear sanderj, fdrake and rnerwein,

thanks for your interest of course, I am really grateful.

> **sanderj said:**
> On what kind of network are you? Home network, or work, or ... ?
Could it be there is a proxy or firewall? 
It's a home network, two ubuntu/GNU linux PCs are connecting to the internet through an ADSL modem/router. The one is working fine, the other is not. I have not activated any proxy or firewall. As you can see above, iptables are clear. Above, executing ps, I cannot recognize something that could cause the problem. :( Also, in gconf-editor system -> http_proxy -> use_http_proxy is unchecked.

> **fdrake said:**
> can you show us your open ports?
```
netstat --listen localhost
```

fdrake, the output is:```
$ netstat --listen localhost
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost.locald:domain *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp        0      0 localhost.localdom:6010 *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN     
tcp6       0      0 madrid:6010             [::]:*                  LISTEN     
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN     
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN     
udp        0      0 localhost.locald:domain *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 192.168.1.25:netbios-ns *:*                                
udp        0      0 madrid.lan:netbios-ns   *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 192.168.1.2:netbios-dgm *:*                                
udp        0      0 madrid.lan:netbios-dgm  *:*                                
udp        0      0 *:netbios-dgm           *:*                                
udp        0      0 *:58048                 *:*                                
udp        0      0 *:mdns                  *:*                                
udp6       0      0 [::]:mdns               [::]:*                             
udp6       0      0 [::]:51625              [::]:*                             
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     6906     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     7482     /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     9713     @/tmp/dbus-ifV1P4V0eG
unix  2      [ ACC ]     STREAM     LISTENING     8924     public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     7385     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     8929     private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     8582     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     8932     private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     7285     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     9732     /tmp/at-spi2/socket-1303-1804289383
unix  2      [ ACC ]     STREAM     LISTENING     8935     private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     10186    /tmp/.esd-119/socket
unix  2      [ ACC ]     STREAM     LISTENING     10188    /var/lib/lightdm/.pulse/c74612d339a57ce109c0419800000008-runtime/native
unix  2      [ ACC ]     SEQPACKET  LISTENING     7061     /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     10904    /var/run/samba/unexpected
unix  2      [ ACC ]     STREAM     LISTENING     8938     private/defer
unix  2      [ ACC ]     STREAM     LISTENING     8941     private/trace
unix  2      [ ACC ]     STREAM     LISTENING     8944     private/verify
unix  2      [ ACC ]     STREAM     LISTENING     8947     public/flush
unix  2      [ ACC ]     STREAM     LISTENING     8950     private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     8953     private/proxywrite
unix  2      [ ACC ]     STREAM     LISTENING     8956     private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     8393     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     8959     private/relay
unix  2      [ ACC ]     STREAM     LISTENING     7371     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     8962     public/showq
unix  2      [ ACC ]     STREAM     LISTENING     8965     private/error
unix  2      [ ACC ]     STREAM     LISTENING     8968     private/retry
unix  2      [ ACC ]     STREAM     LISTENING     8971     private/discard
unix  2      [ ACC ]     STREAM     LISTENING     8974     private/local
unix  2      [ ACC ]     STREAM     LISTENING     8977     private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     8980     private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     8983     private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     8986     private/scache
unix  2      [ ACC ]     STREAM     LISTENING     8989     private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     8992     private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     8995     private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     8998     private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     9001     private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     9004     private/mailman
unix  2      [ ACC ]     STREAM     LISTENING     9660     @/tmp/dbus-efQb45CRqv
unix  2      [ ACC ]     STREAM     LISTENING     8583     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     7419     /var/run/avahi-daemon/socket

```

rnerwein:```
$ nslookup www.google.com
Server:         127.0.0.1
Address:        127.0.0.1#53

Non-authoritative answer:
Name:   www.google.com
Address: 173.194.39.244
Name:   www.google.com
Address: 173.194.39.243
Name:   www.google.com
Address: 173.194.39.240
Name:   www.google.com
Address: 173.194.39.242
Name:   www.google.com
Address: 173.194.39.241

```

rnerwein the message I am getting in firefox after entering the address [www.google.com](www.google.com) is "Unable to connect --- Firefox can't establish a connection to the server at www.google.com."

also, using lynx I get ```
$ lynx www.google.com
Looking up  'www.google.com' first

Looking up www.google.com first
Looking up www.google.com
Making HTTP connection to www.google.com
Alert!: Unable to connect to remote host.

lynx: Can't access startfile http://www.google.com/

```

:(

---

### Post by sanderj on 2013-02-18
If you live-boot Ubuntu from USB-stick or CD, does Internet work?

---

### Post by costis on 2013-02-18
> **sanderj said:**
> If you live-boot Ubuntu from USB-stick or CD, does Internet work?
sanderj I am sorry but I cannot do this. It has no CD/DVD drive or working usb ports.  :frown:  ..., but I put the same cable on the other another pc and is working fine. Also, ssh connection between the two PCs is fine, too.

---

### Post by sanderj on 2013-02-18
> **costis said:**
> sanderj I am sorry but I cannot do this. It has no CD/DVD drive or working usb ports.  :frown:  

How did you install Ubuntu onto the machine? Did you do that, or someone else?

---

### Post by Daniel Smoczyk on 2013-02-18
[costis]("http://ubuntuforums.org/member.php?u=200488"): please try to comment out line (# at line begining) with 'dnsmasq' in /etc/NetworkManager/NetworkManager.conf and reboot computer...

it's a bug someware in ubuntu, i had the same after upgrade to 12.04.2

can You ping i0.wp.com ? I couldn't with enabled dnsmasq...

---

### Post by costis on 2013-02-18
> **sanderj said:**
> How did you install Ubuntu onto the machine? Did you do that, or someone else?

Dear sanderj, it was installed before the cdrom drive stopped working.


> **Daniel Smoczyk said:**
> [costis]("http://ubuntuforums.org/member.php?u=200488"): please try to comment out line (# at line begining) with 'dnsmasq' in /etc/NetworkManager/NetworkManager.conf and reboot computer...
it's a bug someware in ubuntu, i had the same after upgrade to 12.04.2
can You ping i0.wp.com ? I couldn't with enabled dnsmasq...

Dear Daniel Smoczyk,

my /etc/NetworkManager/NetworkManager.conf is ```
[main]
plugins=ifupdown,keyfile
#dns=dnsmasq

no-auto-default=00:C0:9F:2D:A4:C5,

[ifupdown]
managed=false

```

So I tried three versions:
## Version 1 ##
```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

#no-auto-default=00:C0:9F:2D:A4:C5,

[ifupdown]
managed=false

```

## Version 2 ##
```
[main]
plugins=ifupdown,keyfile
#dns=dnsmasq

no-auto-default=00:C0:9F:2D:A4:C5,

[ifupdown]
managed=false

```

## Version 3 ##
```
[main]
plugins=ifupdown,keyfile
#dns=dnsmasq

#no-auto-default=00:C0:9F:2D:A4:C5,

[ifupdown]
managed=false

```

,... but none of the above worked.

I can ping: ```
$ ping  i0.wp.com
PING cs82.wac.edgecastcdn.net (93.184.220.111) 56(84) bytes of data.
64 bytes from 93.184.220.111: icmp_req=1 ttl=60 time=58.4 ms
64 bytes from 93.184.220.111: icmp_req=2 ttl=60 time=57.1 ms
^C64 bytes from 93.184.220.111: icmp_req=3 ttl=60 time=56.8 ms
```

Thanks,....   :confused:

---

### Post by sanderj on 2013-02-18
You have not answered my question what happens after a reboot.

The only thing I can think of is some external device/firewall that is blocking non-ping traffic for your host. 

Furthermore I can't think of anything else.

---

### Post by costis on 2013-02-18
> **sanderj said:**
> You have not answered my question what happens after a reboot.

Dear sanderj, 

sorry I haven't replied directly. I have rebooted the machine many times. 

> **sanderj said:**
> 
The only thing I can think of is some external device/firewall that is blocking non-ping traffic for your host. Furthermore I can't think of anything else.
As I had already stated this is not the case, since I have put the same ethernet cable on another machine that can access internet flawlessly with it afterwards. Thank you very very much for your interest.

---

### Post by sanderj on 2013-02-18
> **costis said:**
> 


As I had already stated this is not the case, since I have put the same ethernet cable on another machine that can access internet flawlessly with it afterwards. Thank you very very much for your interest.

Well, on my Internet modem I can select Parental Control, and block Internet traffic for a certain MAC address. That way I could mimic your problem.

Just saying ... 

So maybe you can pick up your system and connect it to some other network (the neighbour's?), and see what happens.

---

### Post by fdrake on 2013-02-18
> **costis said:**
> Dear sanderj, fdrake and rnerwein,

thanks for your interest of course, I am really grateful.

 
It's a home network, two ubuntu/GNU linux PCs are connecting to the internet through an ADSL modem/router. The one is working fine, the other is not. I have not activated any proxy or firewall. As you can see above, iptables are clear. Above, executing ps, I cannot recognize something that could cause the problem. :( Also, in gconf-editor system -> http_proxy -> use_http_proxy is unchecked.



fdrake, the output is:```
$ netstat --listen localhost
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost.locald:domain *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp        0      0 localhost.localdom:6010 *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN     
tcp6       0      0 madrid:6010             [::]:*                  LISTEN     
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN     
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN     
udp        0      0 localhost.locald:domain *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 192.168.1.25:netbios-ns *:*                                
udp        0      0 madrid.lan:netbios-ns   *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 192.168.1.2:netbios-dgm *:*                                
udp        0      0 madrid.lan:netbios-dgm  *:*                                
udp        0      0 *:netbios-dgm           *:*                                
udp        0      0 *:58048                 *:*                                
udp        0      0 *:mdns                  *:*                                
udp6       0      0 [::]:mdns               [::]:*                             
udp6       0      0 [::]:51625              [::]:*                             
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     6906     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     7482     /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     9713     @/tmp/dbus-ifV1P4V0eG
unix  2      [ ACC ]     STREAM     LISTENING     8924     public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     7385     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     8929     private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     8582     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     8932     private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     7285     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     9732     /tmp/at-spi2/socket-1303-1804289383
unix  2      [ ACC ]     STREAM     LISTENING     8935     private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     10186    /tmp/.esd-119/socket
unix  2      [ ACC ]     STREAM     LISTENING     10188    /var/lib/lightdm/.pulse/c74612d339a57ce109c0419800000008-runtime/native
unix  2      [ ACC ]     SEQPACKET  LISTENING     7061     /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     10904    /var/run/samba/unexpected
unix  2      [ ACC ]     STREAM     LISTENING     8938     private/defer
unix  2      [ ACC ]     STREAM     LISTENING     8941     private/trace
unix  2      [ ACC ]     STREAM     LISTENING     8944     private/verify
unix  2      [ ACC ]     STREAM     LISTENING     8947     public/flush
unix  2      [ ACC ]     STREAM     LISTENING     8950     private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     8953     private/proxywrite
unix  2      [ ACC ]     STREAM     LISTENING     8956     private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     8393     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     8959     private/relay
unix  2      [ ACC ]     STREAM     LISTENING     7371     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     8962     public/showq
unix  2      [ ACC ]     STREAM     LISTENING     8965     private/error
unix  2      [ ACC ]     STREAM     LISTENING     8968     private/retry
unix  2      [ ACC ]     STREAM     LISTENING     8971     private/discard
unix  2      [ ACC ]     STREAM     LISTENING     8974     private/local
unix  2      [ ACC ]     STREAM     LISTENING     8977     private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     8980     private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     8983     private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     8986     private/scache
unix  2      [ ACC ]     STREAM     LISTENING     8989     private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     8992     private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     8995     private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     8998     private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     9001     private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     9004     private/mailman
unix  2      [ ACC ]     STREAM     LISTENING     9660     @/tmp/dbus-efQb45CRqv
unix  2      [ ACC ]     STREAM     LISTENING     8583     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     7419     /var/run/avahi-daemon/socket

```


:(

port http 80 is closed since it is not listed as listening port; did you use any configuration service lately?

---

### Post by rnerwein on 2013-02-19
> **costis said:**
> Dear sanderj, it was installed before the cdrom drive stopped working.




Dear Daniel Smoczyk,

my /etc/NetworkManager/NetworkManager.conf is ```
[main]
plugins=ifupdown,keyfile
#dns=dnsmasq

no-auto-default=00:C0:9F:2D:A4:C5,

[ifupdown]
managed=false

```So I tried three versions:
## Version 1 ##
```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

#no-auto-default=00:C0:9F:2D:A4:C5,

[ifupdown]
managed=false

```## Version 2 ##
```
[main]
plugins=ifupdown,keyfile
#dns=dnsmasq

no-auto-default=00:C0:9F:2D:A4:C5,

[ifupdown]
managed=false

```## Version 3 ##
```
[main]
plugins=ifupdown,keyfile
#dns=dnsmasq

#no-auto-default=00:C0:9F:2D:A4:C5,

[ifupdown]
managed=false

```,... but none of the above worked.

I can ping: ```
$ ping  i0.wp.com
PING cs82.wac.edgecastcdn.net (93.184.220.111) 56(84) bytes of data.
64 bytes from 93.184.220.111: icmp_req=1 ttl=60 time=58.4 ms
64 bytes from 93.184.220.111: icmp_req=2 ttl=60 time=57.1 ms
^C64 bytes from 93.184.220.111: icmp_req=3 ttl=60 time=56.8 ms
```Thanks,....   :confused:
hi
you missed the constitulation with "no" out-commented line (in my configuration is no comment)
ciao

---

### Post by costis on 2013-02-20
> **fdrake said:**
> port http 80 is closed since it is not listed as listening port; did you use any configuration service lately?

Dear fdrake, 

I certainly did not see this coming!

Could I please ask you how to open this port? How can I found out what blocks it?

```
# iptables -A INPUT -p tcp --dport 80 -j ACCEPT

# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
           destination  

# netstat -an | grep "LISTEN "
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::25                   :::*                    LISTEN     
tcp6       0      0 :::445                  :::*                    LISTEN     
tcp6       0      0 :::139                  :::*                    LISTEN 

```

on my other machine port 80 is open ```
#  netstat -an | grep "LISTEN "
(...other ports...)   
tcp        0      0 127.0.0.1:8000          0.0.0.0:*               LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
(...other ports...)
```

No I did not use any configuration service lately, only positive answers to ubuntu 12.04.2 (from 11.10).

```
# ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND                                                                                                                                                                                                                                                    
root         1  0.0  0.1   3672  2024 ?        Ss   14:37   0:00 /sbin/init                                                                                                                                                                                                                                                 
root         2  0.0  0.0      0     0 ?        S    14:37   0:00 [kthreadd]                                                                                                                                                                                                                                                 
root         3  0.0  0.0      0     0 ?        S    14:37   0:00 [ksoftirqd/0]                                                                                                                                                                                                                                              
root         5  0.0  0.0      0     0 ?        S    14:37   0:01 [kworker/u:0]                                                                                                                                                                                                                                              
root         6  0.0  0.0      0     0 ?        S    14:37   0:00 [migration/0]                                                                                                                                                                                                                                              
root         7  0.0  0.0      0     0 ?        S    14:37   0:00 [watchdog/0]                                                                                                                                                                                                                                               
root         8  0.0  0.0      0     0 ?        S<   14:37   0:00 [cpuset]                                                                                                                                                                                                                                                   
root         9  0.0  0.0      0     0 ?        S<   14:37   0:00 [khelper]                                                                                                                                                                                                                                                  
root        10  0.0  0.0      0     0 ?        S    14:37   0:00 [kdevtmpfs]                                                                                                                                                                                                                                                
root        11  0.0  0.0      0     0 ?        S<   14:37   0:00 [netns]                                                                                                                                                                                                                                                    
root        12  0.0  0.0      0     0 ?        S    14:37   0:00 [sync_supers]                                                                                                                                                                                                                                              
root        13  0.0  0.0      0     0 ?        S    14:37   0:00 [bdi-default]                                                                                                                                                                                                                                              
root        14  0.0  0.0      0     0 ?        S<   14:37   0:00 [kintegrityd]                                                                                                                                                                                                                                              
root        15  0.0  0.0      0     0 ?        S<   14:37   0:00 [kblockd]                                                                                                                                                                                                                                                  
root        16  0.0  0.0      0     0 ?        S<   14:37   0:00 [ata_sff]                                                                                                                                                                                                                                                  
root        17  0.0  0.0      0     0 ?        S    14:37   0:00 [khubd]                                                                                                                                                                                                                                                    
root        18  0.0  0.0      0     0 ?        S<   14:37   0:00 [md]                                                                                                                                                                                                                                                       
root        19  0.0  0.0      0     0 ?        S    14:37   0:00 [kworker/u:1]                                                                                                                                                                                                                                              
root        20  0.0  0.0      0     0 ?        S    14:37   0:01 [kworker/0:1]                                                                                                                                                                                                                                              
root        21  0.0  0.0      0     0 ?        S    14:37   0:00 [khungtaskd]                                                                                                                                                                                                                                               
root        22  0.0  0.0      0     0 ?        S    14:37   0:00 [kswapd0]                                                                                                                                                                                                                                                  
root        23  0.0  0.0      0     0 ?        SN   14:37   0:00 [ksmd]                                                                                                                                                                                                                                                     
root        24  0.0  0.0      0     0 ?        SN   14:37   0:00 [khugepaged]                                                                                                                                                                                                                                               
root        25  0.0  0.0      0     0 ?        S    14:37   0:00 [fsnotify_mark]                                                                                                                                                                                                                                            
root        26  0.0  0.0      0     0 ?        S    14:37   0:00 [ecryptfs-kthrea]                                                                                                                                                                                                                                          
root        27  0.0  0.0      0     0 ?        S<   14:37   0:00 [crypto]                                                                                                                                                                                                                                                   
root        35  0.0  0.0      0     0 ?        S<   14:37   0:00 [kthrotld]                                                                                                                                                                                                                                                 
root        57  0.0  0.0      0     0 ?        S<   14:37   0:00 [devfreq_wq]                                                                                                                                                                                                                                               
root       163  0.0  0.0      0     0 ?        S<   14:37   0:00 [firewire]                                                                                                                                                                                                                                                 
root       174  0.0  0.0      0     0 ?        S    14:37   0:00 [scsi_eh_0]                                                                                                                                                                                                                                                
root       175  0.0  0.0      0     0 ?        S    14:37   0:00 [scsi_eh_1]                                                                                                                                                                                                                                                
root       231  0.0  0.0      0     0 ?        S    14:38   0:00 [jbd2/sda2-8]                                                                                                                                                                                                                                              
root       232  0.0  0.0      0     0 ?        S<   14:38   0:00 [ext4-dio-unwrit]                                                                                                                                                                                                                                          
root       307  0.0  0.0   2832   608 ?        S    14:38   0:00 upstart-udev-bridge --daemon                                                                                                                                                                                                                               
root       313  0.0  0.1   3252  1460 ?        Ss   14:38   0:00 /sbin/udevd --daemon
root       449  0.0  0.1   6680  2252 ?        Ss   14:38   0:00 /usr/sbin/sshd -D
102        471  0.0  0.1   3800  1608 ?        Ss   14:38   0:00 dbus-daemon --system --fork --activation=upstart
root       486  0.0  0.1   4744  1332 ?        Ss   14:38   0:00 /usr/sbin/bluetoothd
syslog     493  0.0  0.1  30036  1288 ?        Sl   14:38   0:00 rsyslogd -c5
avahi      507  0.0  0.1   3568  1668 ?        S    14:38   0:00 avahi-daemon: running [madrid.local]
avahi      510  0.0  0.0   3452   432 ?        S    14:38   0:00 avahi-daemon: chroot helper
root       519  0.0  0.0      0     0 ?        S<   14:38   0:00 [krfcommd]
root       520  0.0  0.0   3248  1056 ?        S    14:38   0:00 /sbin/udevd --daemon
root       521  0.0  0.0   3248  1004 ?        S    14:38   0:00 /sbin/udevd --daemon
root       537  0.0  0.2  11072  3412 ?        Ss   14:38   0:00 /usr/sbin/cupsd -F
root       579  0.0  0.0      0     0 ?        S<   14:38   0:00 [kpsmoused]
root       586  0.0  0.0      0     0 ?        S    14:38   0:00 [pccardd]
root       682  0.0  0.3  21404  4788 ?        Ss   14:38   0:00 smbd -F
root       705  0.0  0.1  21484  1328 ?        S    14:38   0:00 smbd -F
root       719  0.0  0.2   7224  2736 ?        Ss   14:38   0:00 /usr/sbin/modem-manager
root       733  0.0  0.3  31124  4836 ?        Ssl  14:38   0:00 NetworkManager
root       747  0.0  0.3  25360  3724 ?        Sl   14:38   0:00 /usr/lib/policykit-1/polkitd --no-debug
root       751  0.0  0.0   2844   376 ?        S    14:38   0:00 upstart-socket-bridge --daemon
root       858  0.0  0.0   4632   832 tty4     Ss+  14:38   0:00 /sbin/getty -8 38400 tty4
root       865  0.0  0.0   4632   836 tty5     Ss+  14:38   0:00 /sbin/getty -8 38400 tty5
root       884  0.0  0.0   4632   828 tty2     Ss+  14:38   0:00 /sbin/getty -8 38400 tty2
root       885  0.0  0.0   4632   828 tty3     Ss+  14:38   0:00 /sbin/getty -8 38400 tty3
root       892  0.0  0.0   4632   840 tty6     Ss+  14:38   0:00 /sbin/getty -8 38400 tty6
root       920  0.0  0.0   2176   688 ?        Ss   14:38   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       922  0.0  0.0   2620   860 ?        Ss   14:38   0:00 cron
daemon     923  0.0  0.0   2468   344 ?        Ss   14:38   0:00 atd
whoopsie   929  0.0  0.3  25932  4360 ?        Ssl  14:38   0:00 whoopsie
root       936  0.0  0.2  33016  2988 ?        Ssl  14:38   0:00 lightdm
root       970  0.5  5.6 104472 68540 tty7     Ss+  14:38   0:44 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -no
root      1011  0.0  0.0      0     0 ?        S    14:38   0:00 [flush-8:0]
root      1038  0.0  0.1   4576  1400 ?        Ss   14:38   0:00 /usr/lib/postfix/master
root      1100  0.0  0.2  18244  3464 ?        Sl   14:38   0:00 lightdm --session-child 16 19
root      1104  0.0  0.2  15836  3192 ?        Sl   14:38   0:00 /usr/lib/accountsservice/accounts-daemon
root      1213  0.0  0.2  29300  3452 ?        Sl   14:38   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1293  0.0  0.1   5728  2260 tty1     Ss   14:38   0:00 /bin/login --       
lightdm   1302  0.0  0.0   2236   528 ?        Ss   14:38   0:00 /bin/sh /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-g
lightdm   1307  0.0  0.0   3808  1052 ?        Ss   14:38   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
lightdm   1308  0.4  1.3 234092 15952 ?        Sl   14:38   0:40 /usr/sbin/unity-greeter
lightdm   1310  0.0  0.2  42452  3112 ?        Sl   14:38   0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher --launch-immediately
lightdm   1315  0.0  0.1   3256  1348 ?        S    14:38   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --n
lightdm   1322  0.0  0.2  17000  2996 ?        Sl   14:38   0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
lightdm   1325  0.0  0.1   8404  2104 ?        S    14:38   0:00 /usr/lib/gvfs/gvfsd
lightdm   1327  0.0  0.2  33736  2544 ?        Sl   14:38   0:00 /usr/lib/gvfs//gvfs-fuse-daemon -f /var/lib/lightdm/.gvfs
lightdm   1334  0.0  0.1  32492  2344 ?        Sl   14:38   0:00 /usr/lib/dconf/dconf-service
lightdm   1340  0.0  0.7  57804  9276 ?        Sl   14:38   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
root      1346  0.0  0.2  28392  3632 ?        Sl   14:38   0:00 /usr/lib/upower/upowerd
colord    1468  0.0  0.8  52364 10048 ?        Sl   14:38   0:00 /usr/lib/i386-linux-gnu/colord/colord
root      1472  0.0  0.1   8864  2360 ?        S    14:38   0:00 lightdm --session-child 12 19
lightdm   1477  0.0  0.3  74416  4804 ?        Sl   14:38   0:00 /usr/lib/indicator-session/indicator-session-service
lightdm   1479  0.0  0.4  70396  5956 ?        Sl   14:38   0:00 /usr/lib/indicator-datetime/indicator-datetime-service
lightdm   1484  0.0  0.3 116444  4740 ?        Sl   14:38   0:00 /usr/lib/indicator-sound/indicator-sound-service
lightdm   1497  0.0  0.1   7980  2304 ?        S    14:38   0:00 /usr/lib/geoclue/geoclue-master
lightdm   1500  0.0  0.2   9924  3400 ?        S    14:38   0:00 /usr/lib/i386-linux-gnu/gconf/gconfd-2
lightdm   1502  0.0  0.3  21336  4292 ?        S    14:38   0:00 /usr/lib/ubuntu-geoip/ubuntu-geoip-provider
lightdm   1506  0.0  0.3  99172  4724 ?        S<l  14:38   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1508  0.0  0.0  21328  1204 ?        SNl  14:38   0:00 /usr/lib/rtkit/rtkit-daemon
lightdm   1515  0.0  0.2  14072  2480 ?        S    14:38   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
root      1855  0.0  0.0      0     0 ?        S    16:28   0:00 [kworker/0:0]
costis    1982  0.0  0.6  11088  7400 tty1     S+   16:36   0:01 -bash
root      2029  0.0  0.1   2928  1224 ?        S    16:36   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.ac
postfix   2140  0.0  0.1   4648  1280 ?        S    16:36   0:00 qmgr -l -t fifo -u
postfix   2141  0.0  0.1   4600  1252 ?        S    16:36   0:00 pickup -l -t fifo -u -c
root      2180  0.0  0.1  13328  1748 ?        Ss   16:36   0:00 nmbd -D
root      2197  0.0  0.2  11872  3588 ?        Ss   16:37   0:00 sshd: costis [priv] 
costis    2295  0.0  0.1  11872  1580 ?        S    16:37   0:00 sshd: costis@pts/0  
costis    2296  0.0  0.6  11080  7388 pts/0    Ss   16:37   0:00 -bash
root      2439  0.0  0.1   7608  1984 pts/0    S    16:40   0:00 sudo bash
root      2440  0.0  0.3   7968  4324 pts/0    S    16:40   0:00 bash
root      2579  0.0  0.0      0     0 ?        S    16:58   0:00 [kworker/0:2]
root      2580  0.0  0.0      0     0 ?        S    16:58   0:00 [kworker/0:3]
root      2581  0.0  0.0   4944  1108 pts/0    R+   16:59   0:00 ps aux

```

ufw is disabled, (but the situation does not alter when I enable it). I am really confused. :confused:
```
# ufw status
Status: inactive

```

---

### Post by costis on 2013-02-20
> **rnerwein said:**
> hi
you missed the constitulation with "no" out-commented line (in my configuration is no comment)
ciao

Dear rnerwein, 

I am sorry but I did not understand you. What do you mean by "constitulation"?

Should I comment something else? (I did not find the bug report you were referring, too).

Of course, thanks to everyone! :) I am really feeling supported by our community! :)

---

### Post by costis on 2013-02-20
> **sanderj said:**
> You have not answered my question what happens after a reboot.
The only thing I can think of is some external device/firewall that is blocking non-ping traffic for your host. 
Furthermore I can't think of anything else.

Dear sanderj, 

thank you very much for your vigorous assistance. As fdrake pointed out, the problem is "internal" and I am trying to find it out...

---

### Post by fdrake on 2013-02-20
can you show us your bing conf:
```

 less /etc/bindresvport.blacklist

```
or maybe you have also the "/etc/named.conf"

---

### Post by costis on 2013-02-20
It's ```
$ cat /etc/bindresvport.blacklist 
#
# This file contains a list of port numbers between 600 and 1024,
# which should not be used by bindresvport. bindresvport is mostly
# called by RPC services. This mostly solves the problem, that a
# RPC service uses a well known port of another service.
#
631     # cups
636     # ldaps
774     # rpasswd
783     # spamd
873     # rsync
921     # lwresd
993     # imaps
995     # pops

$ cat /etc/named.conf
cat: /etc/named.conf: No such file or directory
$ sudo updatedb && locate named.conf
# there is no named.conf in my system.

```

---

### Post by costis on 2013-02-20
> **fdrake said:**
> 
or maybe you have also the "/etc/named.conf"
I am also attaching the results.txt that was created after running net.sh that I 've found in [one]("http://ubuntuforums.org/showthread.php?p=11194893#post11194893") of your posts.

---

### Post by fdrake on 2013-02-21
I am not able to find from your logs and config file the source of the problem. You said that you did not do any deamon/service configuration, so I don't understand how this can happe so suddenly

my last try would be with iptable s again:
```

sudo su
iptables -I INPUT -p tcp --dport 80 --syn -j ACCEPT
iptables -I INPUT -p udp --dport 80 -j ACCEPT
service iptables save
shutdown -P 10 "System will poweroff in 10 sec."

```

if even this does not work then I suggest you a clean reinstall after backing up your stuff. It would be your fastest choice, in my opinion.

Good luck.

---

### Post by costis on 2013-04-06
Thank you for your "good luck"... hehe I was needing it :)

Well after 1+ month I have finally managed to "solve" the issue. I deleted the connection (couldn't find out what was wrong with it, though) using Gnome's Network Manager and created a new one (DHCP and everything as the previous default values). After that I had a normal internet connection. Thank you guys! :)

---

