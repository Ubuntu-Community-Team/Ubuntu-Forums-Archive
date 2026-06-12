---
title: "Google hangouts unable to send out video"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by deadtom on 2013-09-03
I have iptables running on Kubuntu 12.04 on a quad core 3GHz PC with 8GB of RAM.


No devices inside the network are able to send out video to google hangouts. Not PCs, droids, or android tablets. If I disconnect the droids and try over the 4G, they send video fine so it's clearly a network problem.


At first, I assumed this was an iptables issues. After spending considerable time trying to narrow down which specific rule might be the culprit, I simply opened it up, wide open, for testing purposes. Here is the output of iptables -L -v, to verify that everything is open:


```
$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 4 packets, 120 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   23  1724 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpts:tcpmux:65535
   50  9223 ACCEPT     udp  --  any    any     anywhere             anywhere             udp dpts:1:65535
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere            
    0     0 DROP       all  --  eth1   any     anywhere             anywhere            


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 6023 8081K ACCEPT     all  --  eth1   eth0    anywhere             anywhere             state RELATED,ESTABLISHED
 2574  211K ACCEPT     all  --  eth0   eth1    anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere             LOG level warning


Chain OUTPUT (policy ACCEPT 6 packets, 3456 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   12  1456 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpts:tcpmux:65535
   39  7510 ACCEPT     udp  --  any    any     anywhere             anywhere             udp dpts:1:65535
```


Google's support says that is needs ports 80, 443 and 19305 through 19309 for hangouts to work properly. At this point though, this is irrelevant because I've tried opening it up all the way and allowing all traffic through, to no avail.

So I think I can assume that the problem is not with iptables.

I set up some logging in iptables, logging all traffic from one PC during a hangout session, over port 19305, to see if I could get an idea of what's going on, but it's not showing any dropped or invalid packets. In fact, as far as I can tell, this shows that all data is passing back and forth just fine, unless I'm interpreting this wrong:

```
Sep  3 12:48:48 srv1 kernel: [76960.601209] HANGOUT_OUT:IN=eth0 OUT=eth1 MAC=00:14:22:1a:b7:3b:00:11:95:bc:c2:d0:08:00 SRC=192.168.58.40 DST=173.194.79.127 LEN=258 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=36811 DPT=19305 LEN=238
Sep  3 12:48:48 srv1 kernel: [76960.617058] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=141 TOS=0x00 PREC=0x00 TTL=44 ID=43183 PROTO=UDP SPT=19305 DPT=50228 LEN=121
Sep  3 12:48:48 srv1 kernel: [76960.617096] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=62 TOS=0x00 PREC=0x00 TTL=44 ID=43184 PROTO=UDP SPT=19305 DPT=36811 LEN=42
Sep  3 12:48:48 srv1 kernel: [76960.628760] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=850 TOS=0x00 PREC=0x00 TTL=44 ID=43185 PROTO=UDP SPT=19305 DPT=36811 LEN=830
Sep  3 12:48:48 srv1 kernel: [76960.636754] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=850 TOS=0x00 PREC=0x00 TTL=44 ID=43186 PROTO=UDP SPT=19305 DPT=36811 LEN=830
Sep  3 12:48:48 srv1 kernel: [76960.636828] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=849 TOS=0x00 PREC=0x00 TTL=44 ID=43187 PROTO=UDP SPT=19305 DPT=36811 LEN=829
Sep  3 12:48:48 srv1 kernel: [76960.645502] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=156 TOS=0x00 PREC=0x00 TTL=44 ID=43188 PROTO=UDP SPT=19305 DPT=50228 LEN=136
Sep  3 12:48:48 srv1 kernel: [76960.649190] HANGOUT_OUT:IN=eth0 OUT=eth1 MAC=00:14:22:1a:b7:3b:00:11:95:bc:c2:d0:08:00 SRC=192.168.58.40 DST=173.194.79.127 LEN=1190 TOS=0x00 PREC=0x00 TTL=63 ID=37081 PROTO=UDP SPT=36811 DPT=19305 LEN=1170
Sep  3 12:48:48 srv1 kernel: [76960.654170] HANGOUT_OUT:IN=eth0 OUT=eth1 MAC=00:14:22:1a:b7:3b:00:11:95:bc:c2:d0:08:00 SRC=192.168.58.40 DST=173.194.79.127 LEN=67 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=50228 DPT=19305 LEN=47
Sep  3 12:48:48 srv1 kernel: [76960.659172] HANGOUT_OUT:IN=eth0 OUT=eth1 MAC=00:14:22:1a:b7:3b:00:11:95:bc:c2:d0:08:00 SRC=192.168.58.40 DST=173.194.79.127 LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=50228 DPT=19305 LEN=64
Sep  3 12:48:48 srv1 kernel: [76960.659408] HANGOUT_OUT:IN=eth0 OUT=eth1 MAC=00:14:22:1a:b7:3b:00:11:95:bc:c2:d0:08:00 SRC=192.168.58.40 DST=173.194.79.127 LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=55894 DPT=19305 LEN=64
Sep  3 12:48:48 srv1 kernel: [76960.659429] HANGOUT_OUT:IN=eth0 OUT=eth1 MAC=00:14:22:1a:b7:3b:00:11:95:bc:c2:d0:08:00 SRC=192.168.58.40 DST=173.194.79.127 LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=36811 DPT=19305 LEN=64
Sep  3 12:48:48 srv1 kernel: [76960.671742] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=70 TOS=0x00 PREC=0x00 TTL=44 ID=43189 PROTO=UDP SPT=19305 DPT=36811 LEN=50
Sep  3 12:48:48 srv1 kernel: [76960.679487] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=178 TOS=0x00 PREC=0x00 TTL=44 ID=43190 PROTO=UDP SPT=19305 DPT=50228 LEN=158
Sep  3 12:48:48 srv1 kernel: [76960.683656] HANGOUT_OUT:IN=eth0 OUT=eth1 MAC=00:14:22:1a:b7:3b:00:11:95:bc:c2:d0:08:00 SRC=192.168.58.40 DST=173.194.79.127 LEN=159 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=50228 DPT=19305 LEN=139
Sep  3 12:48:48 srv1 kernel: [76960.702722] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=1006 TOS=0x00 PREC=0x00 TTL=44 ID=43191 PROTO=UDP SPT=19305 DPT=36811 LEN=986
Sep  3 12:48:48 srv1 kernel: [76960.703458] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=1006 TOS=0x00 PREC=0x00 TTL=44 ID=43192 PROTO=UDP SPT=19305 DPT=36811 LEN=986
Sep  3 12:48:48 srv1 kernel: [76960.717218] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=86 TOS=0x00 PREC=0x00 TTL=44 ID=43193 PROTO=UDP SPT=19305 DPT=36811 LEN=66
Sep  3 12:48:48 srv1 kernel: [76960.717452] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=66 TOS=0x00 PREC=0x00 TTL=44 ID=43194 PROTO=UDP SPT=19305 DPT=36811 LEN=46
Sep  3 12:48:48 srv1 kernel: [76960.717697] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=1006 TOS=0x00 PREC=0x00 TTL=44 ID=43195 PROTO=UDP SPT=19305 DPT=36811 LEN=986
Sep  3 12:48:48 srv1 kernel: [76960.718699] HANGOUT_IN:IN=eth1 OUT=eth0 MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=173.194.79.127 DST=192.168.58.40 LEN=1007 TOS=0x00 PREC=0x00 TTL=44 ID=43196 PROTO=UDP SPT=19305 DPT=36811 LEN=987
Sep  3 12:48:48 srv1 kernel: [76960.720380] HANGOUT_OUT:IN=eth0 OUT=eth1 MAC=00:14:22:1a:b7:3b:00:11:95:bc:c2:d0:08:00 SRC=192.168.58.40 DST=173.194.79.127 LEN=183 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=UDP SPT=50228 DPT=19305 LEN=163
```


There are two wireless APs on the network but I've verified that the problem persists over ethernet or wireless.

Also[COLOR=#000000][FONT=Verdana], when I'm at work, I tunnel all of my browsing activity through an ssh connection to my house. Hangouts works flawlessly there. The only thing I can derive from this, is that traffic coming into my firewall over my ssh tunnel from work, would not be passing through eth0, which is my internal NIC. I'm not sure what that means, if anything.[/FONT][/COLOR]

The switch that everything connects to, inside the firewall, is just a dumb switch, no management going on or even possible.

Would any one have any suggestions for something else that would be preventing video from being sent out?


Thanks!

---

### Post by deadtom on 2013-09-04
I've just connected my PC directly to the firewall, eliminating the other PCs, switches, APs and devices on the network. The still not sending out video. The problem is definitely with the Kubuntu box.

There has to be someone with an inkling of how to track this down. :(

---

### Post by deadtom on 2013-09-05
I discovered last night that if I start the hangout, invite someone and wait long enough, a picture from my webcam will come up however, it's just a single frame and never seems to progress to an actual video feed of me sitting there.

So this appears to be a case of extreme lag. Everything else works fine, audio, chat and plugins all work fine. Just not video.

I'm running a 100mb network, my cable connection is 18/2 and the PC acting as the firewall should be able to handle the throughput. Clearly though, something is hanging it up.

Still hoping someone has an idea of where to go from here.

---

### Post by deadtom on 2013-09-05
Here is the problem:




```
Sep  5 20:53:52 srv1 kernel: [17316.362778] Invalid packet: IN=eth1 OUT= MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=74.125.161.13 DST=<My IP> LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=80 DPT=46768 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 20:53:53 srv1 kernel: [17316.613384] Invalid packet: IN=eth1 OUT= MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=74.125.161.13 DST=<My IP> LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=80 DPT=46768 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 20:53:53 srv1 kernel: [17317.137580] Invalid packet: IN=eth1 OUT= MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=74.125.161.13 DST=<My IP> LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=80 DPT=46768 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 20:53:54 srv1 kernel: [17318.180523] Invalid packet: IN=eth1 OUT= MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=74.125.161.13 DST=<My IP> LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=80 DPT=46768 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 20:53:55 srv1 kernel: [17319.046480] Invalid packet: IN=eth1 OUT= MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=74.125.161.13 DST=<My IP> LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=80 DPT=46769 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 20:53:56 srv1 kernel: [17320.268026] Invalid packet: IN=eth1 OUT= MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=74.125.161.13 DST=<My IP> LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=80 DPT=46768 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 20:54:00 srv1 kernel: [17324.440652] Invalid packet: IN=eth1 OUT= MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=74.125.161.13 DST=<My IP> LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=80 DPT=46768 WINDOW=0 RES=0x00 RST URGP=0
Sep  5 20:54:09 srv1 kernel: [17332.781812] Invalid packet: IN=eth1 OUT= MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=74.125.161.13 DST=<My IP> LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=80 DPT=46768 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 20:54:25 srv1 kernel: [17349.455201] Invalid packet: IN=eth1 OUT= MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=74.125.161.13 DST=<My IP> LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=80 DPT=46768 WINDOW=0 RES=0x00 RST URGP=0 
Sep  5 20:54:29 srv1 kernel: [17352.974417] Invalid packet: IN=eth1 OUT= MAC=00:14:22:1a:b7:3c:00:13:5f:01:66:3f:08:00 SRC=74.125.161.13 DST=<My IP> LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=80 DPT=46769 WINDOW=0 RES=0x00 RST URGP=0 
```


Every time I start a hangout, syslog gets flooded with these. That IP is a Google IP.  So the question is, why are these packets being classified as invalid? MTU problem?

---

