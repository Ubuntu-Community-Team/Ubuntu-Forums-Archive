---
title: "Poor SMB performance to 10.04 machine"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by mhouston100 on 2010-07-16
Gaaah I'm pulling my hair out over this speed issue from my HTPC. With everything else disconnected I have a Windows 7 machine, a DNS-323 Nas, and a Ubuntu 10.04 machine (with an rtl8111C card)

I'm getting some really weird performance when trying to watch movies on the HTPC (Ubuntu) from the NAS.  I have been testing with iperf and the basic results are.

_Speed between the Windows 7 and Nas performance both ways is_

87Mbit/s - 94Mbits/s (approx)

_Speed between Windows 7 and Ubuntu HTPC_

Windows as client Ubuntu HTPC as server:

200Kbit/s - 1.28 Mbit/s (approx)

Ubuntu HTPC client and Windows 7 as server:

85.5 Mbits/s - 93Mbits/s (approx)

_Speed between Ubuntu HTPC and Nas_

Nas as server Ubuntu HTPC as client:

88Mbit/s - 90Mbit/s

Ubuntu HTPC as server Nas as client:

27Mbit/s - 30Mbit/s

Real world performance doing an ftp transfer from the NAS to the HTPC I think it peaked at around 2MB a second and watching a movie (through VLC or XBMC) would have to buffer every 10 seconds or so.

Transferring or watching from the Windows machine to the NAS is no problemo.

While there are some GB nics in there its all connected through a 100MB switch + Netgear NB6 router.

Anyone have any ideas for me to try, or more info I can provide?

Note:: I also have several other HTPC's connecting through wireless and wired running both Ubuntu 9.10 and Windows XP and they all run perfectly fine.  Even streaming videos over the 54Mb wireless is perfect after the initial buffer.

Thanks in advance
-Matt

---

