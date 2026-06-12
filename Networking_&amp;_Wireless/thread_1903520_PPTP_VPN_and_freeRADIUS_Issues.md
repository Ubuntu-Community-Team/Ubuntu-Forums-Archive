---
title: "PPTP VPN and freeRADIUS Issues"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by itsalexjones on 2012-01-02
Hi All,

I've got a bit of a problem. I've got a Ubuntu server box which is running a PPTP server and a freeRADIUS server (amongst others). I manage it though webmin and daloradius. The VPN server has been running fine until I tried to set it up to use RADIUS as the authentication method.

The client sends the request and the RADIUS server receives it and correctly appears to send the accept packet generating the following console message when i start it in debug mode
```
Sending Access-Accept of id 14 to 127.0.0.1 port 55455
        Framed-Protocol = PPP
        Framed-Compression = Van-Jacobson-TCP-IP
        MS-CHAP2-Success = 0x19533d33373536304342303146414139453732443335414230334130423836343839413543334438393243
        MS-MPPE-Recv-Key = 0x6891147622a7e1d31938d5bd260568e7
        MS-MPPE-Send-Key = 0xa525c25cfd24a983441e57fcc2d8d600
        MS-MPPE-Encryption-Policy = 0x00000002
        MS-MPPE-Encryption-Types = 0x00000004
Finished request 4.

```
However, it appears that the VPN server doesn't get the message as my VPN client always receives the 'VPN Authentication Failed' message.

Can anyone suggest why it might not be working. I'll provide more info/configs if asked.

---

