---
title: "Gigabit network slow samba, ftp, iperf?"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by Shwick2 on 2008-12-12
I'm having many little problems with my gigabit network.

My hard drive reads at 85 MB/s, so why am I downloading from the ftp server at 68 MB/s?  How could I diagnose what is eating those 17 MB/s?

Why does my windows machine have a slow 326 Mbit/s transmit speed compared with ubuntu's transmit speed of 763 Mbit/s when testing with iperf?

Why do I get slow samba speeds?

Windows is connected to Ubuntu with a 6 foot crossover cable.  Both machines are fully updated.

**windows xp3**
motherboard: gigabit ga-965p-ds3
cpu: C2D E4400
hard drives: 250gb seagate, read = 85 MB/s
lan: marvel 8053 Gigabit LAN (onboard, PCI-E)

**ubuntu 8.04 gateway**
motherboard: Asus P5B-MX
cpu: C2D E2160
hard drive: 250gb seagate, read = 85 MB/s
lan: attansic® L1 PCI-E Gigabit LAN controller (onboard, PCI-E)

iperf[LIST]
[*]windows pc downloading from gateway: 763 Mbit/s = 95 MB/s
[*]gateway downloading from windows pc: 326 Mbit/s = 41 MB/s
[/LIST]

ftp[LIST]
[*]windows pc downloading from gateway: 544 Mbit/s = 68 MB/s
[/LIST]

Samba[LIST]
[*]windows pc downloading from gateway: 194 MBit/s = 24 MB/s
[*]gateway downloading from windows pc: 160 MBit/s = 20 MB/s
[/LIST]


smb.conf
```

[global]
        netbios name = SHWICK_GATEWAY
        server string = SHWICK_GATEWAY
        interfaces = lo, eth1
        bind interfaces only = Yes
        map to guest = Bad User
        passdb backend = tdbsam
        syslog only = Yes
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        os level = 65
        preferred master = Yes
        domain master = Yes
        dns proxy = No
        wins support = Yes
        invalid users = root

[Media]
        path = /home/ftp/
        create mask = 0640
        directory mask = 0750
        guest only = Yes
        guest ok = Yes

```

---

### Post by Shwick2 on 2008-12-13
So I found how to make samba faster, I removed "SO_RCVBUF=8192 SO_SNDBUF=8192" from socket options.  I let the tcp stack set the buffer size automatically now.  8192 was too small for a gigabit lan.

But is there any way I can improve the ftp speeds?  The problem is server side, as I tested a download on both windows and from an ubuntu livecd, and both times it was 68 MB/s.

---

