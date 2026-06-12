---
title: "ufw and VPN(ppp0) rules"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by devanl on 2013-07-15
Hello,

I'm trying to create a set of rules for ufw that will prevent traffic when I am disconnected from my VPN connection.  I have set the default to 'deny' and created the following rules:
```
[FONT=arial]user@ubuntu:~$ sudo ufw status numbered[/FONT]
[FONT=arial]Status: active[/FONT]

[FONT=arial]     To                         Action      From[/FONT]
[FONT=arial]     --                         ------      ----[/FONT]
[FONT=arial][ 1] 192.168.0.8                ALLOW IN    Anywhere[/FONT]
[FONT=arial][ 2] Anywhere                   ALLOW OUT   192.168.0.8 (out)[/FONT]
[[ 3] 209.99.21.19]("tel:%5B%203%5D%20209.99.21.19")[FONT=arial]               ALLOW OUT   Anywhere (out)[/FONT]
[FONT=arial][ 4] 1723                       ALLOW OUT   Anywhere (out)[/FONT]
[FONT=arial][ 5] 53                         ALLOW OUT   Anywhere (out)[/FONT]
[FONT=arial][ 6] Anywhere                   ALLOW IN    53[/FONT]
[FONT=arial][ 7] Anywhere                   ALLOW IN    1723[/FONT]
[FONT=arial][ 8] Anywhere on ppp0           ALLOW IN    Anywhere[/FONT]
[FONT=arial][ 9] Anywhere                   ALLOW OUT   Anywhere on ppp0 (out)[/FONT]
[FONT=arial][10] Anywhere/tcp               ALLOW OUT   Anywhere/tcp on ppp0 (out)[/FONT]
[FONT=arial][11] Anywhere/tcp on ppp0       ALLOW IN    Anywhere/tcp[/FONT]
[FONT=arial][12] Anywhere on eth0           ALLOW IN    [/FONT][192.168.1.0/24]("http://192.168.1.0/24")
[FONT=arial][13] [/FONT][192.168.1.0/24]("http://192.168.1.0/24")[FONT=arial] on eth0     ALLOW IN    Anywhere[/FONT]
[FONT=arial][14] 1723                       ALLOW OUT   Anywhere (v6) (out)[/FONT]
[FONT=arial][15] 53                         ALLOW OUT   Anywhere (v6) (out)[/FONT]
[FONT=arial][16] Anywhere (v6)              ALLOW IN    53[/FONT]
[FONT=arial][17] Anywhere (v6)              ALLOW IN    1723[/FONT]
[FONT=arial][18] Anywhere (v6) on ppp0      ALLOW IN    Anywhere (v6)[/FONT]
[FONT=arial][19] Anywhere (v6)              ALLOW OUT   Anywhere (v6) on ppp0 (out)[/FONT]
[FONT=arial][20] Anywhere/tcp (v6)          ALLOW OUT   Anywhere/tcp (v6) on ppp0 (out)[/FONT]
[FONT=arial][21] Anywhere/tcp (v6) on ppp0  ALLOW IN    Anywhere/tcp (v6)[/FONT]
```

These allow the system to establish the VPN connection:
```
[FONT=arial][ 4] 1723                       ALLOW OUT   Anywhere (out)[/FONT]
[FONT=arial][ 5] 53                         ALLOW OUT   Anywhere (out)[/FONT]
[FONT=arial][ 6] Anywhere                   ALLOW IN    53[/FONT]
[FONT=arial][ 7] Anywhere                   ALLOW IN    1723
[/FONT]...
[FONT=arial][14] 1723                       ALLOW OUT   Anywhere (v6) (out)[/FONT]
[FONT=arial][15] 53                         ALLOW OUT   Anywhere (v6) (out)[/FONT]
[FONT=arial][16] Anywhere (v6)              ALLOW IN    53[/FONT]
[FONT=arial][17] Anywhere (v6)              ALLOW IN    1723[/FONT]
```

These are intended to allow traffic on VPN (ppp0):
```
[FONT=arial][ 8] Anywhere on ppp0           ALLOW IN    Anywhere[/FONT]
[FONT=arial][ 9] Anywhere                   ALLOW OUT   Anywhere on ppp0 (out)[/FONT]
[FONT=arial][10] Anywhere/tcp               ALLOW OUT   Anywhere/tcp on ppp0 (out)[/FONT]
[FONT=arial][11] Anywhere/tcp on ppp0       ALLOW IN    Anywhere/tcp
...
[/FONT][FONT=arial][18] Anywhere (v6) on ppp0      ALLOW IN    Anywhere (v6)[/FONT]
[FONT=arial][19] Anywhere (v6)              ALLOW OUT   Anywhere (v6) on ppp0 (out)[/FONT]
[FONT=arial][20] Anywhere/tcp (v6)          ALLOW OUT   Anywhere/tcp (v6) on ppp0 (out)[/FONT]
[FONT=arial][21] Anywhere/tcp (v6) on ppp0  ALLOW IN    Anywhere/tcp (v6)[/FONT]
```

These are intended to allow traffic to LANs:
```
[FONT=arial][ 1] 192.168.0.8                ALLOW IN    Anywhere[/FONT]
[FONT=arial][ 2] Anywhere                   ALLOW OUT   192.168.0.8 (out)
[/FONT]...
[FONT=arial][12] Anywhere on eth0           ALLOW IN    [/FONT][192.168.1.0/24]("http://192.168.1.0/24")
[FONT=arial][13] [/FONT][192.168.1.0/24]("http://192.168.1.0/24")[FONT=arial] on eth0     ALLOW IN    Anywhere[/FONT]
```

For the most part things appear well but a few things still are not making it... ([FONT=arial]yyy.yyy.yyy.yyy is my IP on VPN)[/FONT]
```
[FONT=arial][28444.859428] [UFW BLOCK] IN=ppp0 OUT= MAC= [/FONT][FONT=arial]SRC=[/FONT][x]("tel:190.32.195.151")xx.xxx.xxx.xxx[FONT=arial] DST=yyy.yyy.yyy.yyy[/FONT][FONT=arial] LEN=40 TOS=0x08 PREC=0x20 TTL=238 ID=46914 PROTO=TCP SPT=19780 DPT=39569 WINDOW=0 RES=0x00 ACK RST URGP=0 [/FONT]
[FONT=arial][28444.927610] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=[/FONT][x]("tel:190.32.195.151")xx.xxx.xxx.xxx[FONT=arial] DST=yyy.yyy.yyy.yyy LEN=40 TOS=0x08 PREC=0x00 TTL=239 ID=44339 PROTO=TCP SPT=28234 DPT=57271 WINDOW=0 RES=0x00 ACK RST URGP=0 [/FONT]
[FONT=arial][28469.278680] [UFW BLOCK] IN=ppp0 OUT= MAC= [/FONT][FONT=arial]SRC=[/FONT][x]("tel:190.32.195.151")xx.xxx.xxx.xxx[FONT=arial] DST=yyy.yyy.yyy.yyy [/FONT][FONT=arial]LEN=40 TOS=0x08 PREC=0x00 TTL=239 ID=44501 PROTO=TCP SPT=28354 DPT=57271 WINDOW=0 RES=0x00 ACK RST URGP=0
[/FONT][FONT=arial][32608.821719] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.12 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2[/FONT]
```

Any ideas why these wouldn't be allowed with the given rules?

Thanks,
Devan

---

