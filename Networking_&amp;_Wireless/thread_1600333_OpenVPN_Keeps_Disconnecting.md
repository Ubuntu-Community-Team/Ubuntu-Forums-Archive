---
title: "OpenVPN Keeps Disconnecting"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by LoneSt4r on 2010-10-18
Hello!

I have been using OpenVPN for a couple of weeks now and it serves me very well.  However, after 3-5 minutes, I get the following error message:

```
Inactivity timeout (--ping-restart), restarting
```

From my googling exercize, it seems this does not happen on the Windows client, but only on the Linux client.  I could not find a proper solution or workaround.

My server configuration file includes:

```
keepalive 10 120
```

Does anyone have an idea?

Thanks!

LoneSt4r

---

### Post by SeijiSensei on 2010-10-19
Make sure the client has the same keepalive setting perhaps?

---

### Post by LoneSt4r on 2010-10-20
That was not a bad idea.  Thank you!  I had never seen the setting applied to the client before.

I just tested your idea.  Unfortunately, it does not make any difference when launched from the CLI.  Also, there is no such option in the Network Manager VPN options, which makes me think that it was not intended to be set on the client side.

Any other suggestion?

---

### Post by SeijiSensei on 2010-10-20
Usually I configure the client and server identically except that the client has the "remote" directive and the IP addresses in the "ifconfig" directive are reversed.

In my .conf files I have these directives:
```

ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key

```
and my tunnels always remain up.  Do your configurations have these options enabled as well?

---

### Post by Sven6210 on 2010-10-21
I have general problems establishing OpenVPN connections under Ubuntu for some days now. I am not sure when it exactly started but it affects my Ubuntu 10.04 where I have been using OpenVPN since the beginning without problems as well as Ubuntu 10.10 which I just installed on my Netbook this week. I can not establish the VPN connection with any of the two machines these days.

Any idea?

I will further investigate and try tonight.

---

### Post by LoneSt4r on 2010-10-22
@SeijiSensei: I didn't have the first 3 lines, but I believe the keepalive option would do the same thing.  I tried it anyways, with no effect.

I also tried copying the same configuration on the server side and now everything is down.  I cannot connect anymore.  :(  I will have to find another way to connect to the server to fix this. :(  I am in Saudi Arabia for another 2 weeks before I return home, and I especially needed the VPN for that trip.  

Here is my full configuration:

```
client
dev tun
proto udp
remote XXX.XXX.XXX.XXX 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca /etc/openvpn/ca.crt
cert /etc/openvpn/ubuntu.crt
key /etc/openvpn/ubuntu.key
ns-cert-type server
comp-lzo
verb 3
ping 15
ping-restart 45
ping-timer-rem 
```

---

### Post by SeijiSensei on 2010-10-23
> **SeijiSensei said:**
> Usually I configure the client and server identically **except that the client has the "remote" directive and the IP addresses in the "ifconfig" directive are reversed.**

When you copied the configuration did you remove the "client" and "remote" directives from the server end and reverse the IP addresses in the "ifconfig" directive?   Only one end should have the "client" and "remote" commands.  Since the order of addresses in the "ifconfig" directive is "local_ip remote_ip" they have to be in reverse order on each end.

My configuration file came from a CentOS installation where all those keep-alive settings are the defaults.  I also don't use certificates, just a shared private key.

---

### Post by LoneSt4r on 2010-10-23
The previous post contained my client configuration.  Here is my server configuration:


```
port 1194
proto udp
dev tun
ca ca.crt
cert XX.crt
key XX.key  # This file should be kept secret
dh dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
client-to-client
keepalive 10 120
comp-lzo
persist-key
persist-tun
status openvpn-status.log
verb 3
```

My configs are based on the default examples provided in Ubuntu 10.10.

Could you please post your own full configs so I get an idea of the difference?

Thanks!

---

### Post by SeijiSensei on 2010-10-24
> **LoneSt4r said:**
> Could you please post your own full configs so I get an idea of the difference?

Here's an example for the **client**:

```

dev tun
remote vpnserver.example.com
ifconfig 10.100.1.2 10.100.1.1
secret /etc/openvpn/keys/mysharedkey.key

# I use a non-standard port
port 33333

user nobody
# some distros use group "nobody"; Ubuntu uses "nogroup"
group nogroup

comp-lzo

ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
```

Corresponding **server** file:
```

dev tun

# next is reverse of above
ifconfig 10.100.1.1 10.100.1.2

secret /etc/openvpn/keys/myshared.key
port 33333
user nobody

# this machine runs CentOS with group "nobody"
group nobody

comp-lzo
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key

# a little extra debugging on the server side
verb 3
```

That's it.  I have quite of number of tunnels running with configurations more or less identical to these.

---

