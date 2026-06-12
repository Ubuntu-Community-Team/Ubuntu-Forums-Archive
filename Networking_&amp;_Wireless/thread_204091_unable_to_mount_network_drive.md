---
title: "unable to mount network drive"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by ashrack on 2006-06-26
I'have started converting my Win2k3 server to Ubuntu Dapper (atm double boot). And I have set up DHCP, Internet Sharing, Firewall, aMule. 
But I am unable to mount my client machine which also has UBUNTU DAPPER, heres the error:

```
tom@server:~$ sudo mount -t smbfs //192.168.0.6/c /media/c
mount: wrong fs type, bad option, bad superblock on //192.168.0.6/c,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

tom@server:~$ dmesg | tail
[17187316.472000] Inbound IN=ppp0 OUT= MAC= SRC=193.95.214.72 DST=193.95.249.21 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=51437 DF PROTO=TCP SPT=3737 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
[17187415.352000] Unknown OutputIN= OUT=eth0 SRC=192.168.1.1 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
[17187435.256000] Inbound IN=ppp0 OUT= MAC= SRC=193.95.198.100 DST=193.95.249.21 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=9627 DF PROTO=TCP SPT=1828 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
[17187438.084000] Inbound IN=ppp0 OUT= MAC= SRC=193.95.198.100 DST=193.95.249.21 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=9892 DF PROTO=TCP SPT=1828 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
[17187467.016000] Inbound IN=ppp0 OUT= MAC= SRC=193.95.213.41 DST=193.95.249.21 LEN=64 TOS=0x00 PREC=0x00 TTL=46 ID=43171 DF PROTO=TCP SPT=1936 DPT=139 WINDOW=53760 RES=0x00 SYN URGP=0
[17187467.704000] Inbound IN=ppp0 OUT= MAC= SRC=204.16.208.116 DST=193.95.249.21 LEN=512 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=44913 DPT=1027 LEN=492
[17187469.936000] Inbound IN=ppp0 OUT= MAC= SRC=193.95.213.41 DST=193.95.249.21 LEN=64 TOS=0x00 PREC=0x00 TTL=46 ID=44265 DF PROTO=TCP SPT=1936 DPT=139 WINDOW=53760 RES=0x00 SYN URGP=0
[17187471.160000] Inbound IN=ppp0 OUT= MAC= SRC=193.95.217.233 DST=193.95.249.21 LEN=48 TOS=0x00 PREC=0x00 TTL=125 ID=53762 DF PROTO=TCP SPT=2529 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
[17187474.164000] Inbound IN=ppp0 OUT= MAC= SRC=193.95.217.233 DST=193.95.249.21 LEN=48 TOS=0x00 PREC=0x00 TTL=125 ID=54119 DF PROTO=TCP SPT=2529 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
[17187497.196000] smb_fill_super: missing data argument

```

but ```
tom@server:~$ sudo smbclient //192.168.0.6/c

``` works and also if I boot to W2k3 SERVER I can access the network drive

---

### Post by ashrack on 2006-06-26
fixed it. Forgot to supply the username and password to it

---

