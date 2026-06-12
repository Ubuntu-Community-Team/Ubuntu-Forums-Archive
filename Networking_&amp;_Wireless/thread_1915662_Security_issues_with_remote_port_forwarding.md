---
title: "Security issues with remote port forwarding"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by mirimir on 2012-01-26
I want to host an OpenVPN access server at a VPS that I rent. However, I don't want to run the server there, in order to ensure security of the client credentials. And so I would like to run the server locally, and use remote port forwarding to the VPS. In order to obscure my local IP address, I ssh to the VPS through nested VPN tunnels, using public key authentication.

I'm using thttpd for testing on port 8081. I added "GatewayPorts yes" to /etc/ssh/sshd_config on the VPS and rebooted. Then I forwarded: "ssh -R 8080:localhost:8081 user@my-VPS". The forwarded port is listening globally:

user@my-VPS:~$ netstat -an | grep "LISTEN "
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp6       0      0 :::8080                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     

And my test page is available at "http://my-VPS:8080".

I appreciate that my VPS provider, with cooperation from providers of the VPN services that I'm using, could determine my local IP address. How readily could those acccessing services that I have forwarded do so? Would they need cooperation from my VPS provider?

---

