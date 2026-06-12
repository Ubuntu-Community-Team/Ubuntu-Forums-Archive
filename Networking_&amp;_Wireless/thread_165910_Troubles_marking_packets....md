---
title: "Troubles marking packets..."
date: 2006-04-25
forum: Networking &amp; Wireless
---

### Post by eniacpx on 2006-04-25
I am trying to re-route unknown mac addresses to a local web server for registration,.
Here is what I have right now:
```
#===========================================

iptables -t mangle -F
iptables -t mangle -N MAC

iptables -t mangle -A FORWARD -i ${LAN} -j MAC

for i in `cat /etc/goodHosts`
do
        iptables -t mangle -A MAC -m mac --mac-source $i -j RETURN
done
iptables -t mangle -A MAC -p tcp --dport 80 -j MARK --set-mark 99

iptables -t nat -A PREROUTING -m mark --mark 99 -j DNAT --to 192.168.1.1

#==========================================
```

But for some reason it is not redirecting the packets, everything just works fine. If I change the "DNAT" at the end to a "LOG" it logs nothing, can someone please help me out here?
Thanks!

---

