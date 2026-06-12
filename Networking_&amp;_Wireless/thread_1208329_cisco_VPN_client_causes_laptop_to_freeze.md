---
title: "cisco VPN client causes laptop to freeze"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by b-boy on 2009-07-09
Hi guys I am using the cisco vpn client to connect to my work network from home, so what i do is start the client with 
```
/etc/init.d/vpnclient_init start
```
and then connect with 
```
vpnclient connect mywork
```
then I am asked to accept the disclaimer and i press Y 
I get an ip address and then my laptop freezes and the CAPS LOCK light stays on

Please help :-(

I have tried vpnc but I get the following error 
```
vpnc: quick mode response rejected:  (ISAKMP_N_INVALID_PAYLOAD_TYPE)(1) this means the concentrator did not like what we had to offer.
```

---

### Post by vanadium on 2009-07-09
You should be able to connect to a cisco vpn graphically using network manager. For this, you (may) need to install network-manager-vpnc using Synaptic.

---

### Post by b-boy on 2009-07-09
> **vanadium said:**
> You should be able to connect to a cisco vpn graphically using network manager. For this, you (may) need to install network-manager-vpnc using Synaptic.

I have tried this but is does not work 

error
VPN connection failed

syslog 

```
Jul  9 09:57:30 ubuntu154 kernel: [ 1130.073512] tun0: Disabled Privacy Extensions
Jul  9 09:57:31 ubuntu154 NetworkManager: <info>  VPN plugin failed: 1 
Jul  9 09:57:31 ubuntu154 NetworkManager: <info>  VPN plugin state changed: 6 
Jul  9 09:57:31 ubuntu154 NetworkManager: <info>  VPN plugin state change reason: 0 
Jul  9 09:57:31 ubuntu154 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 

```

---

