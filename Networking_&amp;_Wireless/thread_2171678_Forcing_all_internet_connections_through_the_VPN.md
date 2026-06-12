---
title: "Forcing all internet connections through the VPN"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by gsakkis on 2013-09-01
I've been trying to force my internet connection to go through my VPN (OpenVPN) and disallow access if it's not available, without sucess so far. The closest I found was [this page]("http://askubuntu.com/questions/160048/how-to-force-ubuntu-to-access-the-internet-only-through-a-vpn-and-disable-it-whe") but I still can't get past the VPN. Here's what I did:
- Checked the "Use this connection only for resources on its network" checkbox for my "regular" (non-VPN) connection and verified I cannot connect to the internet at all, including the VPN; that's good.
- Added a static route to my regular connection for my VPN's ip range and verified I can now connect to it; so far so good.
- However I still can't connect to the rest of the internet. I verified that the "Use this connection only for resources on its network" is not checked for my VPN so that's not the reason. What else should I try?

---

### Post by prodigy_ on 2013-09-01
Add default route via your OpenVPN gateway:
```
sudo ip route add default via ip-address # substitute 'ip-address' with the actual gateway IP
```

For initial diagnostics use **mtr** on well-known hosts. Example:
```
mtr -rc 1 8.8.8.8
mtr -rc 1 google.com
```
If **mtr** is not available, use **ping**. Make sure your firewall is not interfering (disable it or add a temporary rule to allow all connections).

---

### Post by gsakkis on 2013-09-01
> **prodigy_ said:**
> Add default route via your OpenVPN gateway:
```
ip route add default via ip-address # substitute 'ip-address' with the actual gateway IP
```


Thanks; how do I find the actual gateway IP?

---

### Post by prodigy_ on 2013-09-01
Is it your own VPN setup? If so, you should configure the VPN server to perform routing and NAT between the tunnel and outside networks. To be honest, I don't even know where to begin explaining because setting up VPN is fairly advanced stuff that requires good knowledge of TCP/IP stack.

If it's provider VPN you should contact the provider support and ask them for connection details.

---

### Post by gsakkis on 2013-09-01
It is a VPN provider. I have the connection details and can connect just fine if I don't check the "Use this connection only for resources on its network" checkbox on my regular wired or wireless interface and don't muck around with routes/netmasks/gateways and other gibberish. The only problem is that when the VPN dies, it falls back to the regular connection and I want to prevent that.

Sorry I'm such a n00b when it comes to networking but is the gateway supposed to be a unique IP for a given VPN provider? Because when I connect normally I seem to be getting a different one each time:

$ netstat -nr | grep tun
0.0.0.0         AAA.BBB.49.1     0.0.0.0         UG        0 0          0 tun0
AAA.BBB.49.0     0.0.0.0         255.255.255.0   U         0 0          0 tun0

$ netstat -nr | grep tun
0.0.0.0         AAA.BBB.45.1     0.0.0.0         UG        0 0          0 tun0
AAA.BBB.45.0     0.0.0.0         255.255.255.0   U         0 0          0 tun0

$ netstat -nr | grep tun
0.0.0.0         AAA.BBB.39.1     0.0.0.0         UG        0 0          0 tun0
AAA.BBB.39.0     0.0.0.0         255.255.255.0   U         0 0          0 tun0

So it looks like the gateway follows a "AAA.BBB.XXX.1" pattern where the AAA.BBB prefix is fixed but the XXX changes.

---

### Post by gsakkis on 2013-09-01
> **gsakkis said:**
> Sorry I'm such a n00b when it comes to networking but is the gateway supposed to be a unique IP for a given VPN provider? Because when I connect normally I seem to be getting a different one each time:

$ netstat -nr | grep tun
0.0.0.0         AAA.BBB.49.1     0.0.0.0         UG        0 0          0 tun0
AAA.BBB.49.0     0.0.0.0         255.255.255.0   U         0 0          0 tun0

$ netstat -nr | grep tun
0.0.0.0         AAA.BBB.45.1     0.0.0.0         UG        0 0          0 tun0
AAA.BBB.45.0     0.0.0.0         255.255.255.0   U         0 0          0 tun0

$ netstat -nr | grep tun
0.0.0.0         AAA.BBB.39.1     0.0.0.0         UG        0 0          0 tun0
AAA.BBB.39.0     0.0.0.0         255.255.255.0   U         0 0          0 tun0

So it looks like the gateway follows a "AAA.BBB.XXX.1" pattern where the AAA.BBB prefix is fixed but the XXX changes.

I think I'm getting closer: the previous output is from when the "Use this connection only for resources on its network" checkbox is **not** checked. When it is checked, I'm getting only one line for tun0, the non-gateway one:

$ netstat -nr |grep tun
AAA.BBB.43.0     0.0.0.0         255.255.255.0   U         0 0          0 tun0

At this point I tried adding manually as default route the AAA.BBB.43.1:

$ sudo ip route add default via AAA.BBB.43.1

Now it all works! I can connect to the VPN, I can access any host through it and when I disconnect it doesn't fall back to the regular connection.

So if I'm not misinterpreting things and this is a correct description of what's happening, the question is how to have a default route be added automatically every time I connect to the VPN, given that the gateway IP is not fixed.

---

### Post by prodigy_ on 2013-09-01
I'd assume there's a checkbox in the settings somewhere but I don't use GUI tools to configure networking.

One possible option is to [use a bash script to establish connection](http://askubuntu.com/questions/43465/how-to-automatically-connect-to-vpn-with-network-manager). Then you could set routes or whatever you need from that script. Something like this:
```
gw_subnet=$(ip route show | grep 'dev tun0' | grep -Eo -m 1 '^([0-9]{1,3}\.){3}')
gw_addr="${gw_subnet}1"
ip route add default via "$gw_addr"
```

---

### Post by gsakkis on 2013-09-03
> **prodigy_ said:**
> I'd assume there's a checkbox in the settings somewhere but I don't use GUI tools to configure networking.

One possible option is to [use a bash script to establish connection]("http://askubuntu.com/questions/43465/how-to-automatically-connect-to-vpn-with-network-manager"). Then you could set routes or whatever you need from that script. Something like this:
```
gw_subnet=$(ip route show | grep 'dev tun0' | grep -Eo -m 1 '^([0-9]{1,3}\.){3}')
gw_addr="${gw_subnet}1"
ip route add default via "$gw_addr"
```

Thanks a lot for the help but honestly I can't mark this as "[solved]" yet. I can't believe how something that should work out of the box or at most be  a checkbox in some GUI requires a custom script hack that needs to be run as root and copied over to all my machines and VMs. I'm certainly not the first one to expect their secure connection to not fall back to their insecure one when the VPN dies so I must be missing something; there has to be an easier way than this.

---

