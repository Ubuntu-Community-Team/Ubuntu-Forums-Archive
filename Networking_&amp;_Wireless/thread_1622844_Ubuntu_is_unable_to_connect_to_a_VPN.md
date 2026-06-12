---
title: "Ubuntu is unable to connect to a VPN"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by shadowers on 2010-11-16
I have an Ubuntu server dedicated to running an openVPN server on my VMware ESX 4 host.  On my Windows clients I am able to connect to the VPN; however, on my Ubuntu 10.10 workstation I am unable to connect.  Here is what I have done.

I have network-manager-openvpn and dependices installed as well as the openvpn package.  When I hit the add button in the network manager for VPNs, I fill out all the needed information, but am unable to hi the apply button.  I have also tried using the openVPN method for connecting.  I download the client.ovpn file from the VPN server, and issue the following command:

```
openvpn --config client.ovpn
```

It asks me for the authentication user and its password and produces this:



```
Mon Nov 15 21:37:20 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Mon Nov 15 21:37:20 2010 Control Channel Authentication: tls-auth using INLINE static key file
Mon Nov 15 21:37:20 2010 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Nov 15 21:37:20 2010 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Nov 15 21:37:20 2010 LZO compression initialized
Mon Nov 15 21:37:20 2010 Control Channel MTU parms [ L:1542 D:166 EF:66 EB:0 ET:0 EL:0 ]
Mon Nov 15 21:37:20 2010 Socket Buffers: R=[126976->200000] S=[126976->200000]
Mon Nov 15 21:37:20 2010 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Mon Nov 15 21:37:20 2010 Local Options hash (VER=V4): '504e774e'
Mon Nov 15 21:37:20 2010 Expected Remote Options hash (VER=V4): '14168603'
Mon Nov 15 21:37:20 2010 UDPv4 link local: [undef]
Mon Nov 15 21:37:20 2010 UDPv4 link remote: 192.168.1.103:1194
Mon Nov 15 21:37:20 2010 TLS: Initial packet from 192.168.1.103:1194, sid=33e077a7 a04daff7
Mon Nov 15 21:37:20 2010 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Mon Nov 15 21:37:20 2010 VERIFY OK: depth=1, /CN=OpenVPN_CA
Mon Nov 15 21:37:20 2010 VERIFY OK: nsCertType=SERVER
Mon Nov 15 21:37:20 2010 VERIFY OK: depth=0, /CN=OpenVPN_Server
Mon Nov 15 21:37:20 2010 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Nov 15 21:37:20 2010 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Nov 15 21:37:20 2010 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Nov 15 21:37:20 2010 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Nov 15 21:37:20 2010 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Mon Nov 15 21:37:20 2010 [OpenVPN_Server] Peer Connection Initiated with 192.168.1.103:1194
Mon Nov 15 21:37:23 2010 SENT CONTROL [OpenVPN_Server]: 'PUSH_REQUEST' (status=1)
Mon Nov 15 21:37:23 2010 PUSH: Received control message: 'PUSH_REPLY,explicit-exit-notify,topology subnet,route-delay 5 30,dhcp-pre-release,dhcp-renew,dhcp-release,route-metric 101,ping 5,ping-restart 40,redirect-gateway def1,redirect-gateway bypass-dhcp,redirect-gateway autolocal,route-gateway 9.2.8.1,dhcp-option DNS 192.168.1.1,register-dns,comp-lzo yes,ifconfig 9.2.8.7 255.255.248.0'
Mon Nov 15 21:37:23 2010 Options error: Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:4: dhcp-pre-release (2.1.4)
Mon Nov 15 21:37:23 2010 Options error: Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:5: dhcp-renew (2.1.4)
Mon Nov 15 21:37:23 2010 Options error: Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:6: dhcp-release (2.1.4)
Mon Nov 15 21:37:23 2010 Options error: Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:15: register-dns (2.1.4)
Mon Nov 15 21:37:23 2010 OPTIONS IMPORT: timers and/or timeouts modified
Mon Nov 15 21:37:23 2010 OPTIONS IMPORT: explicit notify parm(s) modified
Mon Nov 15 21:37:23 2010 OPTIONS IMPORT: LZO parms modified
Mon Nov 15 21:37:23 2010 OPTIONS IMPORT: --ifconfig/up options modified
Mon Nov 15 21:37:23 2010 OPTIONS IMPORT: route options modified
Mon Nov 15 21:37:23 2010 OPTIONS IMPORT: route-related options modified
Mon Nov 15 21:37:23 2010 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Mon Nov 15 21:37:23 2010 ROUTE default_gateway=192.168.1.1
Mon Nov 15 21:37:23 2010 Note: Cannot ioctl TUNSETIFF tun: Operation not permitted (errno=1)
Mon Nov 15 21:37:23 2010 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Mon Nov 15 21:37:23 2010 Cannot allocate TUN/TAP dev dynamically
Mon Nov 15 21:37:23 2010 Exiting
```


Does anyone know how to remedy either if not both of these problems?

---

### Post by deconstrained on 2010-11-16
You do indeed need superuser privileges to create a tun/tap interface for the VPN to run through, hence why it asks for authentication. That may be why you see the error
```
Mon Nov 15 21:37:23 2010 Note: Cannot ioctl TUNSETIFF tun: Operation not permitted (errno=1)
```
The problem could also be that the module hasn't been loaded - 'modprobe tun' would take care of that.

Also...Have you tried writing a configuration file for the client from scratch and using the network-manager's "import" feature instead of downloading an autogenerated client file or setting up an OpenVPN client config using network-manager by itself (because it often fails at this task)? Going through the options/directives one by one WILL help you find the problem, but not without patience. I remember doing exactly this last time I set up a client for my 24/7 box's OVPN and I eventually got it to work, but it's been a long time, so bear with me.

---

