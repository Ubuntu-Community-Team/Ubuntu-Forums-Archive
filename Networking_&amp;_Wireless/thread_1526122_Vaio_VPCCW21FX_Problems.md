---
title: "Vaio VPCCW21FX Problems"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by HrachMD on 2010-07-07
Recently I have bought a new laptop - Sony Vaio VPCCW21FX
but I used to work on linux op-systems and I really hate Win OS.
Unfortunately when I install Ubuntu 10.04 62bit on my laptop I have got 2  problems:
1. with Nvidia card - black screen appears
For installation an alternate CD needed or regular CD but NOMODESET  option must be turned on.
After installation that problem easily solved by installing original  driver from nvidia website over previously installed nvidia driver from  Ubuntu repositories (without last option You have to write nomodeset in  grub conf-s each time when the os booting up).
2. Wireless problem - this is really actual problem which I can't solve.
At first during pinging any IP or rooter AP 40% or 60% packets were only  successful.
I tried everything:
Installing
- backports wireless modules
- compat-wireless drivers (tried all versions - from 2.6.33 to 2.6.35rc)
- even I compiled whole linux kernel (from kernel.org) version 2.6.33  and 2.6.34 but I used configuration file which already had in Ubuntu  10.04
After this changes currently I'm not loosing any packets during pinging  but Internet speed is very slow and strange. May be it is needed to make  changes in configuration file?
Please help me with solving this problem, I really can't migrate to  windows platform.

---

