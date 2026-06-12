---
title: "netstat -uap"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by mosquetero on 2012-07-26
Hi,

I have been suggested to use netstat -uap and netstat -tap to check the services which are being offered by my server. However, I cannot find these flags in the definition of netstat. What do they mean? What is the difference between using -uap and using -udp (I guess the same applies for -tap and -tcp?

Thanks

---

### Post by Cheesehead on 2012-07-26
> **mosquetero said:**
> However, I cannot find these flags in the definition of netstat.

From [FONT="Courier New"]man netstat[/FONT]:
```
SYNOPSIS
       netstat  [address_family_options]  [--tcp|-t]   [--udp|-u]   [--raw|-w]
       [--listening|-l]     [--all|-a]     [--numeric|-n]    [--numeric-hosts]
       [--numeric-ports]           [--numeric-users]           [--symbolic|-N]
       [--extend|-e[--extend|-e]]  [--timers|-o] [--program|-p] [--verbose|-v]
       [--continuous|-c]

```
[FONT="Courier New"]netstat -uap[/FONT] is the equivalent of:
[FONT="Courier New"]netstat --udp --all --program[/FONT]

Does that help?

---

### Post by mosquetero on 2012-07-26
> **Cheesehead said:**
> From [FONT="Courier New"]man netstat[/FONT]:
```
SYNOPSIS
       netstat  [address_family_options]  [--tcp|-t]   [--udp|-u]   [--raw|-w]
       [--listening|-l]     [--all|-a]     [--numeric|-n]    [--numeric-hosts]
       [--numeric-ports]           [--numeric-users]           [--symbolic|-N]
       [--extend|-e[--extend|-e]]  [--timers|-o] [--program|-p] [--verbose|-v]
       [--continuous|-c]

```
[FONT="Courier New"]netstat -uap[/FONT] is the equivalent of:
[FONT="Courier New"]netstat --udp --all --program[/FONT]

Does that help?


Ah! Thanks!! I though you had to use netstat -u -a -p to execute that.

---

