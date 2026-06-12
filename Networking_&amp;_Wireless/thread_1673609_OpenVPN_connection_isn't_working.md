---
title: "OpenVPN connection isn't working"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by EndingPop on 2011-01-22
I have an OpenVPN setup at work, and windows clients are able to connect fine. On my dual-boot system (Windows XP 64-bit and Ubuntu 10.10 64-bit) I'm able to connect on Windows but not Ubuntu. I use the same files for each. The network manager wasn't working, so I'm doing it via the command line right now:

sudo openvpn --config <ovpn file>

Below is the output (sanitized)
```
Sat Jan 22 16:20:31 2011 OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 12 2010
Sat Jan 22 16:20:31 2011 WARNING: --ping should normally be used with --ping-restart or --ping-exit
Sat Jan 22 16:20:31 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sat Jan 22 16:20:31 2011 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Sat Jan 22 16:20:31 2011 LZO compression initialized
Sat Jan 22 16:20:31 2011 Control Channel MTU parms [  ]
Sat Jan 22 16:20:31 2011 TUN/TAP device tap0 opened
Sat Jan 22 16:20:31 2011 TUN/TAP TX queue length set to 100
Sat Jan 22 16:20:31 2011 Data Channel MTU parms [  ]
Sat Jan 22 16:20:31 2011 Local Options hash (VER=V4): 'd79ca330'
Sat Jan 22 16:20:31 2011 Expected Remote Options hash (VER=V4): 'f7df56b8'
Sat Jan 22 16:20:31 2011 Socket Buffers: R=[126976->131072] S=[126976->131072]
Sat Jan 22 16:20:31 2011 UDPv4 link local: [undef]
Sat Jan 22 16:20:31 2011 UDPv4 link remote: [AF_INET] xx.xx.xx.xx:xx
Sat Jan 22 16:20:31 2011 TLS: Initial packet from [AF_INET]xx.xx.xx.xx:xx, sid=4626ea17 0d2b4744
Sat Jan 22 16:20:33 2011 VERIFY OK: depth=1, 
Sat Jan 22 16:20:33 2011 VERIFY OK: nsCertType=SERVER
Sat Jan 22 16:20:33 2011 VERIFY OK: depth=0, 
Sat Jan 22 16:20:34 2011 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sat Jan 22 16:20:34 2011 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sat Jan 22 16:20:34 2011 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sat Jan 22 16:20:34 2011 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sat Jan 22 16:20:34 2011 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Sat Jan 22 16:20:34 2011 [] Peer Connection Initiated with [AF_INET]xx.xx.xx.xx:xx
Sat Jan 22 16:20:35 2011 Initialization Sequence Completed

```
Does this mean it's connected? If so, I'm not able to ping anything on the remote network, not even the OpenVPN server. Anyone have any ideas?

---

### Post by SeijiSensei on 2011-01-23
> **EndingPop said:**
> Sat Jan 22 16:20:35 2011 Initialization Sequence Completed

Does this mean it's connected? If so, I'm not able to ping anything on the remote network, not even the OpenVPN server. Anyone have any ideas?

Looks connected to me. If you type "ifconfig" at the prompt, do you see an tunnel interface like tun0 with an assigned address?  When you say you cannot ping the OpenVPN server, are you pinging it's VPN address, or the machine's external address? You should be able to ping the former, though maybe not the latter.

To reach the remote network, you'll probably need to add a route on the Ubuntu client using a script executed by the "up" directive in the OpenVPN configuration file.  Suppose the Ubuntu VPN endpoint is 10.10.10.2 and the server's endpoint is 10.10.10.1.  SUppose also that the remote network is 192.168.1.0/24.  Then the "up" command should run a script with this command:

```
ip route add 192.168.1.0/24 via 10.10.10.1
```

That will send traffic for the remote network over the tunnel.  For details on the "up" command, use "man openvpn" and search for "--up".

---

### Post by EndingPop on 2011-01-23
Thanks for the quick response, but I'm not really sure if that's the issue. Here's some more information:

1. I can ping the external IP of the VPN entry point before and after connecting (of course).
2. After connecting, here is the output of ifconfig -a
```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:70:b7:3a:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Memory:f6fe0000-f7000000 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:2e:ec:dc  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe2e:ecdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:335253 errors:2 dropped:0 overruns:0 frame:308572
          TX packets:296600 errors:98 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:349673380 (349.6 MB)  TX bytes:166606904 (166.6 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:356742 (356.7 KB)  TX bytes:356742 (356.7 KB)

tap0      Link encap:Ethernet  HWaddr c6:57:15:ba:c3:de  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:10818 (10.8 KB)  TX bytes:0 (0.0 B)

```
My home network is a 192.168.1.* and the VPN should assign an IP in the 10.0.0.* range. None of the adapters got a 10.0.0.* address.

I also tried using the --up command with the command you suggested and got the following: ```
RTNETLINK answers: Operation not permitted
```

So what else can I check?

---

### Post by SeijiSensei on 2011-01-23
Well, since there's no IP assigned to the tap0 interface, you don't have a VPN yet.

I've only built OpenVPN tunnels using Linux's "tun" interface.  Is there a reason why you're using the "tap" interface instead?  May we see the contents of the configuration file you're using?

Also, I thought you were trying to reach a remote network.  You need to replace 192.168.1.0/24 in my routing command example with the address and subnet mask of the remote network.  (The one at work, I presume?)

Are you running a firewall of some kind on the Ubuntu box?  If so, you'll need to open the port you're using for the VPN.

---

### Post by EndingPop on 2011-01-26
Oops, I didn't really know what the route command was doing.

I don't have a firewall up on the ubuntu box either. Here's the config file for the client:
```
tls-client
dev tap
proto udp
remote XX.XX.XX.XX 443
resolv-retry infinite
nobind
persist-key
persist-tun
ca XX.crt
cert XXX.crt
key XXX.key
ns-cert-type server
comp-lzo
verb 3
float
ping 30

```

I'm using a tap interface because that's what the ovpn file I was given uses. It's fine with tap on Windows.

---

