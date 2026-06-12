---
title: "MoBlock blocking port in whitelist range"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by sbussy89 on 2010-02-10
I whitelitsted ports 21 and 50000-60000 in MoBlock to allow for passive ftp on my network. Here is my blockcontrol.conf:

```

# blockcontrol.conf - configuration file for blockcontrol

# This file is sourced by a shell script. Any line which starts with a # (hash)
# is a comment and is ignored. If you set the same variable several times,
# then only the last line will be used.

# Refer to blockcontrol.defaults (/usr/lib/blockcontrol/blockcontrol.defaults)
# for the complete set of possible configuration variables with comments.

# Do a "blockcontrol restart" (sometimes even "reload" is enough) when you have
# edited this file.

WHITE_TCP_OUT="http https ftp ssh 137 138 139 50000:60000 5900 9091"
WHITE_TCP_IN="http https ftp ssh 137 138 139 50000:60000 5900 9091"
WHITE_UDP_OUT="137 138 139"
WHITE_UDP_IN="137 138 139"
WHITE_LOCAL="2"

```

And here is the TCP portion of the packet being blocked:

```

Source port: ftp (21)
Destination port: 51745 (51745)

```

51745 is definitely in the range 50000-60000, so why is it being blocked?

---

### Post by jre on 2010-02-11
Hmm, on the first glance I don't know. Please post your "blockcontrol status", so that we can see whether your configuration really got applied. You may also check your logfiles (/var/log/blockcontrol.log).
Further you can check, whether it is really moblock, and whether it is really that port (I don't know how you figured that out), by using the extended logging to syslog. See here: [https://help.ubuntu.com/community/MoBlock#How%20do%20I%20find%20out%20which%20IP%20or%20port%20was%20blocked?](https://help.ubuntu.com/community/MoBlock#How%20do%20I%20find%20out%20which%20IP%20or%20port%20was%20blocked?)

Besides that, I think you have got a massive overkill with port whitelisting. Especially the incoming ports need only to be whitelisted, when you have got a server running, that listens on these ports (e.g. apache for http, ...)

---

### Post by sbussy89 on 2010-02-12
Hey JRE... here is my blockcontrol status:

```

Current IPv4 iptables rules (this may take a while):

Chain INPUT (policy ACCEPT 6710K packets, 3751M bytes)
 pkts bytes target     prot opt in     out     source               destination         
   13  1655 blockcontrol_in  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW mark match !0x14 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 blockcontrol_fw  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW mark match !0x14 

Chain OUTPUT (policy ACCEPT 7575K packets, 4081M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    2   258 blockcontrol_out  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW mark match !0x14 

Chain blockcontrol_fw (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           mark match 0xa 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.1         
    0     0 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Chain blockcontrol_in (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           mark match 0xa 
    0     0 RETURN     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:139 
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:137 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:50000:60000 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8112 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:5900 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:138 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:137 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:21 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
   13  1655 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Chain blockcontrol_out (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           mark match 0xa reject-with icmp-port-unreachable 
    0     0 RETURN     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     all  --  *      *       0.0.0.0/0            192.168.1.1         
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:139 
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:137 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:50000:60000 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8112 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:5900 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:138 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:137 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:21 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    2   258 NFQUEUE    all  --  *      *       0.0.0.0/0            0.0.0.0/0           NFQUEUE num 92

Please check if the above printed iptables rules are correct!

 * moblock is running
PID: 10508    CMD: /usr/bin/moblock -p /var/lib/blockcontrol/guarding.p2p -q 92 -t -r 10 -a 20 /var/log/moblock.log

 * blockcontrol.wd is running
PID: 10516    CMD: /bin/sh /usr/bin/blockcontrol.wd



```

I used `tail -f /var/log/moblock.log` to see that moblock was blocking the packet, and used wireshark to determine the port it was being sent on. Thanks for any help!

---

### Post by jre on 2010-02-14
The relevant iptables rules are inserted correctly to blockcontrol_out and blockcontrol_in. So we can rule out a bug or misconfiguration.

Do you have MoBlock installed on your router? Then you have to use the FORWARD chain, not IN or OUT. I still recommend you use the extended logging to syslog, to really see what's happening. See the link to the wiki that I alreeady posted. Further I think you have many unnecessary whitelisting rules, thus greatly reducing moblock's protection.

Whitelisting IN traffic is only necessary, when you run a server application on the moblock machine. (e.g. apache webserver listening on port 80)
OUT is for a client on the moblock machine (e.g. surfing the web with firefox on port 80)
FORWARD is for routers, when both client and server are on other machines.

Generally I recommend to prefer IP whitelisting over port whitelisting, because it is much more specific.
As an exemption from this rule do NOT whitelist your LAN on FORWARD, because this would allow ALL FORWARD traffic, also that to and from the internet.

SO if you need further help please read the wiki, and then feel free to ask questions. Then I should know, what you exactly want to do (which is your moblock machine, where does the traffic originate (clients), what are the servers)

---

### Post by sbussy89 on 2010-02-14
MoBlock is running on the Ubuntu server, the same machine that has the FTP server. I have lots of people uploading from multiple locations, so unfortunately IP whitelisting is not an option as it would be a nearly infinite list of IPs.

---

### Post by sbussy89 on 2010-02-14
Something odd happening now... MoBlock logs are no longer showing that I am being blocked, but FTP works when MoBlock is off and doesn't work when MoBlock is on, so it must be the firewall.

---

### Post by jre on 2010-02-15
> **sbussy89 said:**
> MoBlock is running on the Ubuntu server, the same machine that has the FTP server. I have lots of people uploading from multiple locations, so unfortunately IP whitelisting is not an option as it would be a nearly infinite list of IPs.

Good, in this case you really need port whitelisting.

> **sbussy89 said:**
> Something odd happening now... MoBlock logs are no longer showing that I am being blocked, but FTP works when MoBlock is off and doesn't work when MoBlock is on, so it must be the firewall.

Perhaps the logfile just had it's daily rotation. When this happens while you are following the file with "tail -f" you will not get any new loglines. Just try again.

I tested whitelisting multiple ports here. It definitely works! So I am quite sure that you just need to make a few more changes to your configuration.

So I can only recommend again to try the extended logging in order to figure out what really gets blocked (copy and paste from the wiki):

First you need to set in /etc/blockcontrol/blockcontrol.conf
```
LOG_IPTABLES="LOG --log-level info"
```
and do a
```
sudo blockcontrol restart
```
Then you can issue
```
sudo tail -f /var/log/syslog
```.

Before doing those tests I further recommend to wipe out most of your current port whitelistings. For passive ftp I would only start with
```
WHITE_TCP_IN="21"
```
Then you can add those ports that you figure out with the extended port whitelisting, but only for IN or OUT.

---

