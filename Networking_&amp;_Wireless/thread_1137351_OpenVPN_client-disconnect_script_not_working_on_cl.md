---
title: "OpenVPN client-disconnect script not working on client disconnection"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by vanmortel on 2009-04-25
Hi people,

I set up an OpenVPN server on my Ubuntu 8.04

Everything works fines. I have a the client-connect option enable with a connect script that do some work depending on the CN. 

And, on disconnection of that client, I want to run a script to clean up. It is very simple job and the script are good. But the --client-disconnect options only work on openvpn shutdown and not on client disconnection! 

According to the Openvpn 2.1 man page, it's says that the script is executed if the --connect-script return 0 and on client instance shutdown. The connect script return 0 for sure because otherwise, the client can't connect. But instance shutdown... I can't believe it's the daemon of Openvpn... and checked, there is no child process spawn by openvpn for client.

So, help me out please on how to do this?

Here is my configuration :
```

client-connect scripts/connect-client.py
client-disconnect scripts/disconnect-client.py

script-security 2

local X.X.X.X --> (MY_IP)
mode server

port 1194

proto udp

dev tun

ca easy-rsa/keys/ca.crt
cert easy-rsa/keys/server.crt
key easy-rsa/keys/server.key  

dh easy-rsa/keys/dh2048.pem

server 10.8.0.0 255.255.255.0

ifconfig-pool-persist ipp.txt

client-config-dir ccd

keepalive 10 120

cipher BF-CBC           # Blowfish (default)
keysize 448             # Max Blowfish

comp-lzo

;user nobody
group nogroup

persist-key
persist-tun
status openvpn-status.log
verb 3

```

Thanks all!
David

---

