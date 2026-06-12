---
title: "Configure dante SOCKS server to route through VPN"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by PHaLaNX on 2010-08-31
Hello,

I'm trying to configure dante so that it only connects to the internet through the PPTP VPN interface (which is ppp1). My configuration file is currently like this: 

```
internal: 127.0.0.1 port = 3333
external: ppp1
method: username none
logoutput: stderr
user.notprivileged: abc

client pass {
  from: 127.0.0.0/8 port 1-65535 to: 0.0.0.0/0
  log: connect disconnect
}

client block {
  from: 0.0.0.0/0 to: 0.0.0.0/0
  log: connect disconnect error
}

block {
  from: 0.0.0.0/0 to: 127.0.0.0/8
  log: connect disconnect error
}

pass {
  from: 127.0.0.0/8 to: 0.0.0.0/0
  command: connect udpassociate
  log: connect disconnect error
  protocol: tcp udp
}

block {
  from: 0.0.0.0/0 to: 0.0.0.0/0
  log: connect error
}

```

Then I enter 127.0.0.1:3333 as a SOCKS5 proxy in Firefox but for some no connection happens. Here is the dante output when I try to connect google.com. 

```

Aug 31 18:09:30 (1283267370) danted[25978]: pass(1): tcp/accept [: 127.0.0.1.51714 -> 127.0.0.1.3333
Aug 31 18:09:30 (1283267370) danted[25984]: created new requestchild
Aug 31 18:0
Thanks...9:30 (1283267370) danted[25979]: pass(2): tcp/connect [: 127.0.0.1.51714 -> 74.125.39.106.80

```

I tested the interface ppp1 and I'm sure it's OK. Should I add an iptables entry, maybe a route entry? Can anyone give a clue?

---

### Post by PHaLaNX on 2010-08-31
Anyone?

---

