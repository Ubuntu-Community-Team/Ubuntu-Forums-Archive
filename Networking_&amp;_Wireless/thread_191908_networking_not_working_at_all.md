---
title: "networking not working at all"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by ashrack on 2006-06-08
I have 4 identical machines at home. And on the 1. PC I have set UBUNTU DAPPER just the way I want it. So then I cloned this machine with latest ACRONIS TRUE IMAGE to the second machine. And on this second machine all works except NIC isnt even loaded. So I only have LOOPBACK as an option under ifconfig.

Here's the 'lspci -v' of the 1. machine:
[ATTACH]10855[/ATTACH]

ANd this is of the second or cloned machine:
[ATTACH]10856[/ATTACH]

What to do to regain NIC capabilities

ps. this is what the diff command come up:
```
tom@tom:~/Desktop$ diff lspci.txt lspci2.txt
8c8
<       Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
---
>       Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 193
40c40
<       Flags: bus master, medium devsel, latency 0, IRQ 177
---
>       Flags: bus master, medium devsel, latency 0, IRQ 185
46c46
<       Flags: bus master, medium devsel, latency 32, IRQ 185
---
>       Flags: bus master, medium devsel, latency 32, IRQ 177

```

---

### Post by Ivan Matveich on 2006-06-08
Try commenting out all the entries in /etc/iftab on the second machine and rebooting.

If that does not work, reply with your "dmesg" log and the output from "ifconfig -a".

---

### Post by ashrack on 2006-06-08
[QUOTE=Ivan Matveich]Try commenting out all the entries in /etc/iftab on the second machine and rebooting.

If that does not work, reply with your "dmesg" log and the output from "ifconfig -a".[/QUOTE]
tanx that worked great

hopefully it will also work on the other machines

---

