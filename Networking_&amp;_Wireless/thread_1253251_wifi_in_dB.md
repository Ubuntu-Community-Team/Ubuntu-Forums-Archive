---
title: "wifi in dB?"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by ARhere on 2009-08-29
Hello All,

I am looking for a simple and free software tool, (*Linux app, windows app, google gadget, whatever...* that reports wifi signal strength in decibels in real time.

Anyone?  -AR

P.S.  I am testing out different hand made directional antennas and the little bars don't show much information.

---

### Post by tgalati4 on 2009-08-30
cat /proc/net/wireless

I think "level" is expressed in dB.  (-54 on my laptop)

tgalati4@tpad-Gloria7 ~ $ cat /proc/net/wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
  eth1: 0000   75.  -54.  -90.       0      0      0      3      0        5

You can write a script that collects data every so often and dump it to a file.

---

