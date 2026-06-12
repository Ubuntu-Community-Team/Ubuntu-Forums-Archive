---
title: "IP Tables script.."
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by dogatemycomputer on 2009-04-29
Greetings,

I am working on hardening a server for a small office (several people - low call volume) that contains Asterisk (among other services). The physical network topology is:

<INTERNET>
<CHEAP DSL ROUTER>
<24 PORT SWITCH>
<ASTERISK><IP330s><SEVERAL COMPUTERS><VPN SERVER>

The cheap dsl router forwards 5060-5080 and 10,000-20,000 to the Asterisk box. 443 is forwarded to the VPN server. The road worriers tunnel to the VPN server then launch their softphones to connect to the Asterisk server which prevents their passwords from being sent/received in clear text.

I'm a big fan of KISS (keep it simple - stupid). I want to use iptables to simply filter out all traffic unless it originates on the local LAN or the IP of the VoIP providers. My concern is the bolded line below. Wouldn't that simply match and accept all traffic?

I'm not even sure if this script will work. If there are any flaws in my work then I greatly appreciate your input.

The iptables script is:

INTERNAL_NETWORK="192.168.10.0/24"
CALLCENTRIC="204.11.192.0/24"
VOIPVOIP1="74.208.29.0/24"
VOIPVOIP2="69.90.209.0/24"
/sbin/iptables --flush
/sbin/iptables --delete-chain
/sbin/iptables -A INPUT -s $INTERNAL_NETWORK -j ACCEPT
/sbin/iptables -A INPUT -s $CALLCENTRIC -j ACCEPT
/sbin/iptables -A INPUT -s $VOIPVOIP1 -j ACCEPT
/sbin/iptables -A INPUT -s $VOIPVOIP2 -j ACCEPT
/sbin/iptables -P INPUT DROP

The iptables rules list is:

[root@localhost ~]# iptables -L
Chain INPUT (policy DROP)
target prot opt source destination
**ACCEPT all -- anywhere anywhere**
ACCEPT all -- 192.168.10.0/24 anywhere
ACCEPT all -- 204.11.192.0/24 anywhere
ACCEPT all -- 74.208.29.0/24 anywhere
ACCEPT all -- 69.90.209.0/24 anywhere

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination
ACCEPT all -- anywhere anywhere

Thank you in advance for the help!

---

