---
title: "VPN in Ubuntu 9.10"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by xluryan on 2009-11-10
I am having an issue connecting to an IPSec based VPN server. Below is the output from /var/log/syslog. Can anyone point me in the right direction? Please?

```

Nov 10 13:44:47 test-server-0 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.vpnc'...
Nov 10 13:44:47 test-server-0 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 10189
Nov 10 13:44:47 test-server-0 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections
Nov 10 13:44:47 test-server-0 NetworkManager: <info>  VPN plugin state changed: 1
Nov 10 13:44:50 test-server-0 NetworkManager: <info>  VPN plugin state changed: 3
Nov 10 13:44:50 test-server-0 NetworkManager: <info>  VPN connection 'myVPNServer' (Connect) reply received.
Nov 10 13:44:50 test-server-0 kernel: [ 2489.641331] tun0: Disabled Privacy Extensions
Nov 10 13:44:50 test-server-0 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Nov 10 13:44:50 test-server-0 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.



Nov 10 13:45:05 test-server-0 NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Nov 10 13:45:05 test-server-0 NetworkManager: <info>  VPN plugin failed: 1
Nov 10 13:45:05 test-server-0 NetworkManager: <info>  VPN plugin state changed: 6
Nov 10 13:45:05 test-server-0 NetworkManager: <info>  VPN plugin state change reason: 0
Nov 10 13:45:05 test-server-0 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Nov 10 13:45:05 test-server-0 NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf
Nov 10 13:45:05 test-server-0 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov 10 13:45:18 test-server-0 NetworkManager: <debug> [1257882318.001119] ensure_killed(): waiting for vpn service pid 10189 to exit
Nov 10 13:45:18 test-server-0 NetworkManager: <debug> [1257882318.001237] ensure_killed(): vpn service pid 10189 cleaned up

```

---

### Post by rykasimba on 2009-11-20
I am having the same issue for Cisco VPN - any ideas?

---

### Post by infecticide on 2009-11-20
Same issue here.

---

### Post by dheninger on 2009-11-30
Has any one solved this?

I had a fully functional VPN client working until this morning around 10, then nada!!

Any help would be greatly appreciated.

BTW:  I am working inside of a virtual machine, but like I said, it has been working for months!!

TIA
D

---

### Post by Ogref on 2009-12-03
I too was working fine... 2 days ago according to my syslog...  Tonight, Nothing.

I'm unable to find any updates that I ran that may have interfered with Network Manager and/or vpnc via terminal. 

I deleted the keyring file...
I deleted the Network Manager config
I deleted the .conf for vpnc...

On the plus side... I have an excuse why I cannot connect to my office network...

---

### Post by Ogref on 2009-12-08
I was able to resolve the cisco VPN problem through 'vpnc'

I edited the .conf file to read as follows

```
IPSec gateway [domain.name]
IPSec ID [id]
IPSec secret [secret]
Xauth username [local.domain.username]
NAT Traversal Mode cisco-udp
```note the last line of the .conf file.  

I am still unable to log into my Cisco VPN via the Network manager, but it's working perfectly for terminal... 

Has anyone figured out the solution for the Network Manager problem?

---

### Post by lotharmat on 2009-12-09
I changed the encryption to 'Weak - Use with caution' and it worked perfectly..

---

### Post by latashiyf on 2010-01-02
I have been bothered by the same problem. I just started to use Ubuntu 9.10. network-manager-vpnc WORKS WELL at first. Then it suddenly stopped working about 2 hours ago.

If I connect from network manager, system log shows,
[ 3398.672282] tun0: Disabled Privacy Extensions

If I use command line (using the .conf posted above), error shows,
vpnc-connect: no response from target

I have tried to lower the security in the configuration, reinstall network manager/vpnc, disabled the firewall, still won't work.

Any help is greatly appreciated!

---

### Post by vangop on 2010-06-02
Hi!
I had exactly the same thing, vpnc was working from both NM and CLI.
then suddenly stopped. all the profiles, with all settings. Same thing in the dmesg and logs. Same vpnc-connect: no response from target
The issue was simple - I enabled the firewall on the gateway and probably it wasn't on the ruleset. I didn't check the logs to fix yet, but right after disabling the FW on the router - all works just fine.
Hope that helps somebody. ;)

---

### Post by rdeleonp on 2010-12-16
> **lotharmat said:**
> I changed the encryption to 'Weak - Use with caution' and it worked perfectly..

Worked great here (10.04 x86 32-bit).

---

