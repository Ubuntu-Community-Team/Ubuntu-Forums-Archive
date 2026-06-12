---
title: "IPTABLES review"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by smeerbartje on 2012-11-06
I use the following script to configure IPTABLES on my home server. The server has two NICs, eth0 for the INTERNAL network and eth1 for the WAN network (connected to my cable modem). NAT translation is working perfect, so far no problems!! However, when run the "sudo iptables -L" command, I see something strange. please see the contents of the 2nd code tag below. As you can see the default behaviour for the input chain is to DROP everything. But what does the red colored line tell me? Accept everything on all protocolls on all sources for every destination??? This doesn't look okay to me, is it? And my second question: do you guys have any more suggestions? Is my server (and the clients on the internal network connecting through it) safe with this iptables rule set?

Config script:

[FONT="Courier New"][SIZE="2"]#!/bin/sh
echo "Clear old firewall rules..."
iptables --flush
iptables --flush FORWARD
iptables --flush INPUT
iptables --flush OUTPUT
iptables --table nat --flush
iptables --table nat --delete-chain
iptables --table mangle --flush
iptables --table mangle --delete-chain
iptables --delete-chain

echo "Drop all INPUT and FORWARD..."
iptables -P INPUT DROP
iptables -P FORWARD DROP

echo "Drop all IPv6 traffic..."
ip6tables -P INPUT DROP
ip6tables -P OUTPUT DROP
ip6tables -P FORWARD DROP

echo "Accept everything on lo and eth0 (local network)..."
iptables -A INPUT -i lo -p all -j ACCEPT
iptables -A OUTPUT -o lo -p all -j ACCEPT
iptables -A INPUT -i eth0 -p all -j ACCEPT -s 192.168.1.0/24
iptables -A OUTPUT -o eth0 -p all -j ACCEPT -d 192.168.1.0/24

echo "IP Forwarding and Routing for gateway use..."
iptables -A FORWARD -o eth1 -i eth0 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

echo "Enable Packet Forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward

echo "Maintain established connections..."
iptables -A INPUT --in-interface eth1 --match conntrack --ctstate ESTABLISHED,RELATED --jump ACCEPT

echo "Logging rules...(prefix should be iptables)"
#iptables -A INPUT -p tcp --dport 80 --syn -j LOG --log-prefix "iptables: "
#iptables -A INPUT -p tcp --dport 22 --syn -j LOG --log-prefix "iptables: "
#iptables -A INPUT -j LOG --log-level debug --log-prefix "iptables: ** Dropped ** "
iptables -A INPUT -j LOG --log-level debug --log-prefix "[IPTABLES DROP] :"

echo "Allow port 80 (www) and 22 (SSH) connections to the firewall..."
# start SSH anti brute force.
# Iptables tracks every new connection on port 22. When some one from the same IP
# connects 5 times within 600 seconds the IP will be automatically banned for 600 seconds
iptables -A INPUT -p tcp -i eth1 --dport 22 -m state --state NEW -m recent --set --name SSH
iptables -A INPUT -p tcp -i eth1 --dport 22 -m state --state NEW -m recent --update --seconds 600 --hitcount 5 --rttl --name SSH -j DROP
iptables -A INPUT -p tcp -i eth1 --dport 22 -j ACCEPT
# end SSH anti brute force
iptables -A INPUT -p tcp -i eth1 --dport 80 -j ACCEPT

#echo "Allow ping requests..."
#iptables -A INPUT -p icmp --icmp-type 8 -s 0/0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
[/SIZE][/FONT]

Output iptables -L command:

[FONT="Courier New"][SIZE="2"]Chain INPUT ([COLOR="Red"]policy DROP[/COLOR])
target     prot opt source               destination
[COLOR="Red"]ACCEPT     all  --  anywhere             anywhere[/COLOR]
ACCEPT     all  --  192.168.1.0/24       anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
LOG        tcp  --  anywhere             anywhere             tcp dpt:sshflags: FIN,SYN,RST,ACK/SYN LOG level warning prefix "[iptables]: "
           tcp  --  anywhere             anywhere             tcp dpt:ssh state NEW recent: SET name: SSH side: source
DROP       tcp  --  anywhere             anywhere             tcp dpt:ssh state NEW recent: UPDATE seconds: 600 hit_count: 5 TTL-Match name: SSH side: source
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  192.168.1.0/24       anywhere             ctstate NEW
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             192.168.1.0/24[/SIZE][/FONT]

---

### Post by SeijiSensei on 2012-11-06
You need to run "iptables -L -v" to see the complete output.  Without the verbose switch, it doesn't show which interface each rule applies to.  The line that concerns you applies to the localhost interface.  It corresponds to the rule 
```
iptables -A INPUT -i lo -p all -j ACCEPT
```
at the top of your ruleset.

---

### Post by smeerbartje on 2012-11-06
> **SeijiSensei said:**
> You need to run "iptables -L -v" to see the complete output.  Without the verbose switch, it doesn't show which interface each rule applies to.  The line that concerns you applies to the localhost interface.  It corresponds to the rule 
```
iptables -A INPUT -i lo -p all -j ACCEPT
```
at the top of your ruleset.
Thanks! Didn't know of that switch :). So now my concerns are gone... think my server is safe, right? Any other suggestions?

---

### Post by Doug S on 2012-11-06
I would suggest putting this rule:```
iptables -A INPUT -j LOG --log-level debug --log-prefix "[IPTABLES DROP] :"
```at the end of the INPUT chain, rather than in the middle.
 
You have a good SSH identify and block rule set, that a lot of people use. However, you have written yours a little odd, using an extra rule that isn't really needed. I would also suggest a slight modification and eliminate the port 22 spefication from the DROP rule. While admittedly rare, sometimes attackers hammer more than the SSH port at the same time, so once a bad IP is identified, why not drop everything from them? Here is my rule set for, basically the same thing:```
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT

```You allow port 80 in, so I assume you also have a website running on your server. Does that mean you have a static external IP address? If yes, you might consider to use SNAT instead of MASQUERADE, however it doesn't matter that much. Example:```
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP
```Since you already have an ESTABLISHED, RELATED accept on your INPUT chain, I would be tempted to only allow NEW port 80 INPUT, instead of all.
 
For your OUPUT chain, suggest a deafult policy of DROP. That would force you to specifically deal with all your expected senarios with rules. However, that is up to you, as many use a default policy of ACCEPT.
 
It depends on how far you want to go, but you might want to consider: Checking and DROPping INVALID incoming or forwarding tcp packets; Checking for unroutable (RFC1918 ) packets in your forward chain, as some clients (my sons PS3 for example) seem clueless as to such things; Checking for NEW TCP incoming, without the proper SYN flag combination...

---

### Post by smeerbartje on 2012-11-07
Thanks Doug, great help! I've replaced my SSH rules with yours and also modified the port 80 rule to to only accept NEW connections: iptables -A INPUT -i eth1 -p tcp --dport 80 -m state --state NEW -j ACCEPT

I think this set of rules is good for me. Do you think that I'm safe?

---

