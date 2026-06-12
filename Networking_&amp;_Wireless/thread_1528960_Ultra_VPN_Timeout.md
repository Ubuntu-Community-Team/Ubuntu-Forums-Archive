---
title: "Ultra VPN Timeout"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by nicki20048 on 2010-07-11
When trying to connect to UltraVPN recently on Ubuntu 10.04 I have been getting a timeout everytime. I set it up according to [http://www.kabatology.com/11/24/how-to-setup-open-source-ultravpn-in-ubuntu/](http://www.kabatology.com/11/24/how-to-setup-open-source-ultravpn-in-ubuntu/)

Any ideas would be appreciated.

This is my log:

> Sun Jul 11 18:27:06 2010 OpenVPN 2.1_rc9 i686-pc-mingw32 [SSL] [LZO2] [PKCS11] built on Jul 31 2008 
Sun Jul 11 18:27:28 2010 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info. 
Sun Jul 11 18:27:28 2010 LZO compression initialized 
Sun Jul 11 18:27:28 2010 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ] 
Sun Jul 11 18:27:28 2010 RESOLVE: NOTE: servers24.ultravpn.fr resolves to 2 addresses, choosing one by random 
Sun Jul 11 18:27:28 2010 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ] 
Sun Jul 11 18:27:28 2010 Local Options hash (VER=V4): '41690919' 
Sun Jul 11 18:27:28 2010 Expected Remote Options hash (VER=V4): '530fdded' 
Sun Jul 11 18:27:28 2010 Socket Buffers: R=[0->0] S=[0->0] 
Sun Jul 11 18:27:28 2010 UDPv4 link local: [undef] 
Sun Jul 11 18:27:28 2010 UDPv4 link remote: 87.98.164.142:24 
Sun Jul 11 18:27:43 2010 TLS Error: TLS key negotiation failed to occur within 15 seconds (check your network connectivity) 
Sun Jul 11 18:27:43 2010 TLS Error: TLS handshake failed 
Sun Jul 11 18:27:43 2010 TCP/UDP: Closing socket 
Sun Jul 11 18:27:43 2010 SIGUSR1[soft,tls-error] received, process restarting 
Sun Jul 11 18:27:43 2010 Restart pause, 2 second(s) 
Sun Jul 11 18:27:45 2010 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info. 
Sun Jul 11 18:27:45 2010 Re-using SSL/TLS context 
Sun Jul 11 18:27:45 2010 LZO compression initialized 
Sun Jul 11 18:27:45 2010 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ] 
Sun Jul 11 18:27:46 2010 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ] 
Sun Jul 11 18:27:46 2010 Local Options hash (VER=V4): '41690919' 
Sun Jul 11 18:27:46 2010 Expected Remote Options hash (VER=V4): '530fdded' 
Sun Jul 11 18:27:46 2010 Socket Buffers: R=[0->0] S=[0->0] 
Sun Jul 11 18:27:46 2010 UDPv4 link local: [undef] 
Sun Jul 11 18:27:46 2010 UDPv4 link remote: 87.98.157.45:54 
Sun Jul 11 18:27:58 2010 TCP/UDP: Closing socket 
Sun Jul 11 18:27:58 2010 SIGTERM[hard,] received, process exiting

---

