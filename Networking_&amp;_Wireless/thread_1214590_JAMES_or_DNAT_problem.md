---
title: "JAMES or DNAT problem?"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by Decoy on 2009-07-16
Hey everyone,

need experts' help!

I've got:
[LIST]
[*]server1 - server box somewhere on the Internet
[*]server2 - server with Apache James behind the Ubuntu NAT box
[/LIST]
Here's Ubuntu's netfilter ruleset representing DNAT:
```
...
iptables -A FORWARD -d $INT_IP -i $WAN_IF -o $INT_IF -j ACCEPT
iptables -t nat -A PREROUTING -d $EXT_IP -i $WAN_IF -j DNAT --to-destination $INT_IP
...
```
I'm sure that NAT/DNAT works fine because I can access the Internet from server2 and I also can connect to James SMTP module on server2 (`telnet server2 25` is ok), but `telnet server2 110` gives a "Connection refused" error just after short delay. Why I am thinking it's an DNAT problem? I've started `nc -l 2424` on server2 and successfully telneted from server1 on port 2424, but if listening by netcat port is privieleged (i.e. `nc -l 24`) then `telnet server2 24` from server1 gives same "Connection refused" error. But still... Why 25, 80 and 443 ports are DNATed successfully?! I'm stuck.

Here's extract from James' config.xml:
```
   <pop3server enabled="true">
      <port>110</port>
      <handler>
         <helloName autodetect="false">XXX.YYY</helloName>
         <connectiontimeout>120000</connectiontimeout>
      </handler>
   </pop3server>
```

---

### Post by Decoy on 2009-07-16
Hold on a second. Looks like the problem is in server1's firewall! I'll check this and write back...

---

### Post by Decoy on 2009-07-16
Yes, it was server1's firewall, sorry.

---

