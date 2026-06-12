---
title: "Eror with NAT?"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by cmacia06 on 2013-04-26
I asked this question a few days ago but.. i got no reply. Maybe i did'nt put enough information or something... Well i've gotten a little closer to my problem.
So I have my modem connected to my server through usb. Then i have my router connect to my server through ethernet. I am doing this to forward to the router (To monitor and control traffic). The router is the internal network and modem is the external. My modem (eth1) provides the ip through dhcp and i set my router (eth0) to a static ip. I set this in the interfaces file. Once the interfaces are up and have their ip set, I run a script that activates everything that is need to make the server nat capable. BUT.... this does not work. It fails. If i replace the modem with my phones tethering (usb0) it works. Its something that has to do with the modem. But I cannot find out what the modem is doing wrong.

Here is my information

ifconfig 
```

eth0      Link encap:Ethernet  HWaddr 00:30:67:41:0c:3a  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:67ff:fe41:c3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3523402 (3.5 MB)  TX bytes:2967175 (2.9 MB)

eth1      Link encap:Ethernet  HWaddr 00:14:04:e7:24:b7  
          inet addr:72.191.165.30  Bcast:255.255.255.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:297270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:149936774 (149.9 MB)  TX bytes:9342291 (9.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21396 (21.3 KB)  TX bytes:21396 (21.3 KB)

```

The NAT script

```

echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe

EXTIF="eth1"
INTIF="eth0"
#INTIF2="eth0"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"

#======================================================================
#== No editing beyond this line is required for initial MASQ testing == 
echo -en "   loading modules: "
echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a
echo "----------------------------------------------------------------------"
echo -en "ip_tables, "
$MODPROBE ip_tables
echo -en "nf_conntrack, " 
$MODPROBE nf_conntrack
echo -en "nf_conntrack_ftp, " 
$MODPROBE nf_conntrack_ftp
echo -en "nf_conntrack_irc, " 
$MODPROBE nf_conntrack_irc
echo -en "iptable_nat, "
$MODPROBE iptable_nat
echo -en "nf_nat_ftp, "
$MODPROBE nf_nat_ftp
echo "----------------------------------------------------------------------"
echo -e "   Done loading modules.\n"
echo "   Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "   Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr 
echo "   Clearing any existing rules and setting default policy.."

iptables-restore <<-EOF
*nat
-A POSTROUTING -o "$EXTIF" -j MASQUERADE
COMMIT
*filter
:INPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
-A FORWARD -i "$EXTIF" -o "$INTIF" -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 
-A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT
-A FORWARD -j LOG
COMMIT
EOF

echo -e "\nrc.firewall-iptables v$FWVER done.\n"

```

The problem is that everything looks like its fine... (It even ping and everything through a clent computer on the router) but when i try to connect to a web address it hang for about about 3 minutes and then just times out.
The server's internet connection works so i know that it is just not forwarding the modems connection. It almost like it blocking port 80 but my ip tables says it is forwarding all the ports.

iptables -L

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere             LOG level warning

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```

---

### Post by cmacia06 on 2013-04-26
AHA! I may have found an issue here! After a tcpdump i noticed something very stange...

This was in quite a few of those lines!
14:04:51.422926 ARP, Reply chris-A770E3.local is-at 00:30:67:41:0c:3a (oui Unknown), length 28
.........................................................................................................(oui Unknown).................

After some googling this is baisically saying that it doesnt know who to send this packet to. This seems to be the reason why i cant get anything to work, BEACAUSE THEY ARE BEING DROPED! Now.. for my next issue... what do i do with this knoledge?

And its not just that line.. it is also giving that error to my router and server. The server being chris-A770E3.local and router being 192.168.0.1
This leads me to believe that the server isnt correctly converting the mac address during nat. Is there somewhere that i can adjust this?

---

### Post by Doug S on 2013-04-27
I am not convinced that your issues are to do with the ARP level traffic. I think you are using tcpdump in a mode where it tries to lookup everything. I never use it that way, but I did for a test and got a similar result when a name lookup (or whatever) did not work:```
12:00:37.664147 ARP, Request who-has s10.smythies.com tell doug-xps2.smythies.com, length 46
12:00:38.207095 ARP, Request who-has s15.smythies.com tell ns1.smythies.com, length 28
12:00:38.207247 ARP, Reply s15.smythies.com is-at ff:ff:ff:ff:ff:ff [COLOR=#ff0000](oui Unknown), [/COLOR]length 46
12:00:38.916462 ARP, Request who-has s10.smythies.com tell doug-xps2.smythies.com, length 46

```To avoid lookup issues, I typically run tcpdump this way:```
sudo tcpdump -n -nn -tttt -i eth0
```I recognize your iptables rules set as somoething similar to what I started with. However, it is not clear to me what is wrong. When you say:> The router is the internal network and ...You mean the router is this server itself, don't you? Have you tried using tcpdump to follow a packet from some local computer, say one at 192.168.0.10 (or whatever you actually have) to your server at eth0 and also observe it being re-transmitted, with NAT, on eth1? Similarly for the return path?

Edit: Here is the same tcpdump stuff as above without lookups:```
doug@doug-64:~$ sudo tcpdump -n -nn -tttt -i eth0 | grep ARP
2013-04-27 12:15:45.794491 ARP, Request who-has 192.168.111.102 tell 192.168.111.101, length 46
2013-04-27 12:15:45.983093 ARP, Request who-has 192.168.111.112 tell 192.168.111.1, length 28
[COLOR=#ff0000]2013-04-27 12:15:45.983246 ARP, Reply 192.168.111.112 is-at ff:ff:ff:ff:ff:ff, length 46[/COLOR]
2013-04-27 12:15:57.029499 ARP, Request who-has 192.168.111.102 tell 192.168.111.101, length 46
2013-04-27 12:15:57.635204 ARP, Request who-has 192.168.111.102 tell 192.168.111.101, length 46
2013-04-27 12:15:58.665015 ARP, Request who-has 192.168.111.102 tell 192.168.111.101, length 46

```

---

