---
title: "How to disable IPv6 on specific interface?"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by iX9 on 2011-05-26
Hi!
When I run OpenVPN server - tap0 adapter, it breakes Teredo(Miredo) IPv6 address down. I dont need IPv6 on OpenVPN, so is there any way to disable IPv6 on tap0 completely?

---

### Post by novinick on 2011-06-11
try first to see ipv6 adress of tap0

```
ifconfig tap0
```

show's something like this:
>  inet6 addr: **fe80::1234:0000:0000:0000/128** Scope:Link

and then delete it

```
sudo ip -6 addr del fe80::1234:0000:0000:0000/128 dev tap0
```

---

### Post by iX9 on 2011-06-16
OK, this works for current instance.

After restart openvpn or system restart, there is another ipv6 address, probably randomly set.

How to write a script, witch determines this ipv6 address, after openvpn starts and disables it?

---

