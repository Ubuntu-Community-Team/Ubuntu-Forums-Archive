---
title: "DHCP and ebtables"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by rockballad on 2012-06-17
Hello,

If I have a file of IP/Mac table like below, how can I make DHCP server assign IP for corresponding MAC?

```
192.168.0.102 A2:AA:BB:1F:90:A5
192.168.0.103 A2:AA:BB:A8:FC:50
192.168.0.104 A2:AA:BB:B1:11:43
192.168.0.105 A2:AA:BB:66:85:D8
192.168.0.106 A2:AA:BB:E2:61:05
192.168.0.107 A2:AA:BB:91:6E:6F
```

I've heard about ebtables and/or iptable but I don't understand the rule. Can you help me please?

Thank you in advance.

---

### Post by CharlesA on 2012-06-17
It depends on what dhcp server software you are using.

It looks like [ebtables]("http://ebtables.sourceforge.net/") is just an ethernet bridge/firewall and it doesn't do DHCP from looking at the features.

iptables doesn't have anything to do with dhcp either, it's just a firewall.

What DHCP server are you using?

---

### Post by rockballad on 2012-06-17
Hello CharlesA,

I setup DHCP Server on my machine (tried with Ubuntu 10.04 server and CentOS 5.5). I've just hard-coded Mac Addresses inside dhcpd.conf. Something like this:

```

subnet 192.168.1.0 netmask 255.255.255.0 {
   ......
   host user01 {
      hardware ethernet A1:B2:C3:A1:B2:C3;
      fixed-address 192.168.1.100;
   }
}
```

Look like it works. Tomorrow I'll test on my Lab @college. Do you think it's ok?

Thanks for your reply and helping me format the code. I'll notice next time!

---

### Post by CharlesA on 2012-06-17
That looks like the correct syntax. I haven't used dhcpd, but it looks right from looking here:
[http://www.daemon-systems.org/man/dhcpd.conf.5.html](http://www.daemon-systems.org/man/dhcpd.conf.5.html)

---

