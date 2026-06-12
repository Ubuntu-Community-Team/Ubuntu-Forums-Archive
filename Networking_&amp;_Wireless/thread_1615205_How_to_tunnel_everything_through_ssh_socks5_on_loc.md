---
title: "How to tunnel everything through ssh socks5 on localhost 1080"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by xapient on 2010-11-06
i managed to tunnel single apps through the socks 5 when they support socks5 configuration and some other applications with the help of "proxychains"

```
ssh -D 1080 user@host
proxychains someapp
```

BUT  i want all traffic to go through the socks5 without further configuration or the need of proxychains..  
also i want to set the machine as default gateway for other machines so their traffic is going through the socks5 too...

there has to be an iptables rule for that..

all i want to do is route everything through the ssh tunnel at 127.0.0.1:1080  !

i tried to redirect everything except 127.0.0.0 to port 1080 with
```
sudo iptables -t nat -A OUTPUT ! -d 127.0.0.0/8 -p udp -j REDIRECT --to 1080
```
(same for PREROUTING and tcp) but i just got myself offline :(


what do i have to do? is it possible with iptables to solve this "problem" ?
thx for your help !!

---

### Post by xapient on 2010-11-18
oke... i solved this with openvpn redirect gateway option
[http://flexible.xapient.net/?p=606](http://flexible.xapient.net/?p=606)


```
*sudo ssh -C -L 1100:hostIP:1100 root@hostIP -p 443*
```

this line forwards port 1100 on localhost to hostIP:1100 where the openvpn server listens..
the openvpn client connects to localhost:1100 and the redirect gateway option does the rest...

an other solution i found was an ssh vpn  

```
ssh -w 0:0 root@host -p 443 
```
more infos here: [https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

---

