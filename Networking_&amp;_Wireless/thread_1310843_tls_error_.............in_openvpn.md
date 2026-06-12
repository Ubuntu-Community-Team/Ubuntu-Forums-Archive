---
title: "tls error .............in openvpn"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by eshi14 on 2009-11-02
hi all,

i am tryin to configure openvpn in same network my client and server are in same private network.
i gt the initialization sequence completed in server 


[B]Mon Nov  2 14:44:51 2009 WARNING: you are using user/group/chroot without persist-tun -- this may cause restarts to fail
Mon Nov  2 14:44:51 2009 WARNING: you are using user/group/chroot without persist-key -- this may cause restarts to fail
Mon Nov  2 14:44:51 2009 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Mon Nov  2 14:44:51 2009 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Mon Nov  2 14:44:51 2009 Control Channel MTU parms [ L:1585 D:138 EF:38 EB:0 ET:0 EL:0 ]
Mon Nov  2 14:44:51 2009 Data Channel MTU parms [ L:1585 D:1450 EF:53 EB:4 ET:32 EL:0 ]
Mon Nov  2 14:44:51 2009 Local Options hash (VER=V4): 'de2e4cc8'
Mon Nov  2 14:44:51 2009 Expected Remote Options hash (VER=V4): '97d200af'
Mon Nov  2 14:44:51 2009 NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Mon Nov  2 14:44:51 2009 Socket Buffers: R=[112640->131072] S=[112640->131072]
Mon Nov  2 14:44:51 2009 UDPv4 link local (bound): [undef]:1194
Mon Nov  2 14:44:51 2009 UDPv4 link remote: 192.168.100.102:1194
Mon Nov  2 14:44:51 2009 TLS: Initial packet from 192.168.100.102:1194, sid=c3e25faa e3f36766
Mon Nov  2 14:44:51 2009 VERIFY ERROR: depth=1, error=self signed certificate in certificate chain: /C=US/ST=CA/L=SanFrancisco/O=Fort-Funston/CN=Fort-Funston_CA/emailAddress=me@myhost.mydomain
Mon Nov  2 14:44:51 2009 TLS_ERROR: BIO read tls_read_plaintext error: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
Mon Nov  2 14:44:51 2009 TLS Error: TLS object -> incoming plaintext read error
Mon Nov  2 14:44:51 2009 TLS Error: TLS handshake failed
Mon Nov  2 14:44:51 2009 TCP/UDP: Closing socket
Mon Nov  2 14:44:51 2009 SIGUSR1[soft,tls-error] received, process restarting
Mon Nov  2 14:44:51 2009 Restart pause, 2 second(s)
Mon Nov  2 14:44:53 2009 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Mon Nov  2 14:44:53 2009 WARNING: you are using user/group/chroot without persist-tun -- this may cause restarts to fail
Mon Nov  2 14:44:53 2009 WARNING: you are using user/group/chroot without persist-key -- this may cause restarts to fail
Mon Nov  2 14:44:53 2009 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Mon Nov  2 14:44:53 2009 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Mon Nov  2 14:44:53 2009 Control Channel MTU parms [ L:1585 D:138 EF:38 EB:0 ET:0 EL:0 ]
Mon Nov  2 14:44:53 2009 Data Channel MTU parms [ L:1585 D:1450 EF:53 EB:4 ET:32 EL:0 ]
Mon Nov  2 14:44:53 2009 Local Options hash (VER=V4): 'de2e4cc8'
Mon Nov  2 14:44:53 2009 Expected Remote Options hash (VER=V4): '97d200af'
Mon Nov  2 14:44:53 2009 Socket Buffers: R=[112640->131072] S=[112640->131072]
Mon Nov  2 14:44:53 2009 UDPv4 link local (bound): [undef]:1194
Mon Nov  2 14:44:53 2009 UDPv4 link remote: 192.168.100.102:1194
Mon Nov  2 14:44:53 2009 TLS: Initial packet from 192.168.100.102:1194, sid=c2c63932 b9ec75c0
Mon Nov  2 14:44:53 2009 VERIFY ERROR: depth=1, error=self signed certificate in certificate chain: /C=US/ST=CA/L=SanFrancisco/O=Fort-Funston/CN=Fort-Funston_CA/emailAddress=me@myhost.mydomain
Mon Nov  2 14:44:53 2009 TLS_ERROR: BIO read tls_read_plaintext error: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
Mon Nov  2 14:44:53 2009 TLS Error: TLS object -> incoming plaintext read error
Mon Nov  2 14:44:53 2009 TLS Error: TLS handshake failed
[/B]..
.
.
.
.
.
.
.
.
Mon Nov  2 14:53:48 2009 TLS Error: Unroutable control packet received from 192.168.100.102:1234 (si=3 op=P_CONTROL_V1)
Mon Nov  2 14:53:48 2009 TLS Error: Unroutable control packet received from 192.168.100.102:1234 (si=3 op=P_CONTROL_V1)
Mon Nov  2 14:53:48 2009 TLS Error: Unroutable control packet received from 192.168.100.102:1234 (si=3 op=P_CONTROL_V1)
Mon Nov  2 14:53:48 2009 TLS Error: Unroutable control packet received from 192.168.100.102:1234 (si=3 op=P_CONTROL_V1)
Mon Nov  2 14:53:48 2009 TLS Error: Unroutable control packet received from 192.168.100.102:1234 (si=3 op=P_CONTROL_V1)


if someone can help me with the error .....

---

### Post by stealth. on 2011-12-08
Don't mean to revive a old thread, but I found this thread through Google.   Anyways read, [http://www.nrtm.de/index.php/2011/06/08/ssl-fun/](http://www.nrtm.de/index.php/2011/06/08/ssl-fun/)  Simply put, the time on the 2 servers may be different.

---

