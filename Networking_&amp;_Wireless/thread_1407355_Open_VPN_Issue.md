---
title: "Open VPN Issue"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by magul on 2010-02-15
Hi i have question.

I'm trying to connect OpenVPN server using shell command.

I've installed all needed packages (I guess)

if type

```
sudo openvpn client.ovpn
```and i've got messages:

```

Mon Feb 15 12:29:25 2010 OpenVPN 2.1_rc19 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Mon Feb 15 12:29:25 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Mon Feb 15 12:29:25 2010 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Mon Feb 15 12:29:26 2010 LZO compression initialized
Mon Feb 15 12:29:26 2010 Control Channel MTU parms [ L:1574 D:138 EF:38 EB:0 ET:0 EL:0 ]
Mon Feb 15 12:29:26 2010 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Mon Feb 15 12:29:26 2010 Local Options hash (VER=V4): 'd79ca330'
Mon Feb 15 12:29:26 2010 Expected Remote Options hash (VER=V4): 'f7df56b8'
Mon Feb 15 12:29:26 2010 Socket Buffers: R=[114688->131072] S=[114688->131072]
Mon Feb 15 12:29:26 2010 UDPv4 link local: [undef]
Mon Feb 15 12:29:26 2010 UDPv4 link remote: XX.XX.XX.XX:1194
Mon Feb 15 12:29:26 2010 TLS: Initial packet from XX.XX.XX.XX:1194, sid=59c62b34 9f2205b4
Mon Feb 15 12:29:26 2010 VERIFY OK: depth=1, /C=XX/ST=XXX/L=Cit/O=MyCompany/CN=MyCompany_CA/emailAddress=my@email.com
Mon Feb 15 12:29:26 2010 VERIFY OK: nsCertType=SERVER
Mon Feb 15 12:29:26 2010 VERIFY OK: depth=0, /C=XX/ST=XXX/L=City/O=MyCompany/CN=server/emailAddress=my@email.com
Mon Feb 15 12:29:27 2010 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Feb 15 12:29:27 2010 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Feb 15 12:29:27 2010 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Feb 15 12:29:27 2010 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Feb 15 12:29:27 2010 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Mon Feb 15 12:29:27 2010 [server] Peer Connection Initiated with XX.XX.XX.XX:1194
Mon Feb 15 12:29:28 2010 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Mon Feb 15 12:29:28 2010 PUSH: Received control message: 'PUSH_REPLY,ping 15,ping-restart 60'
Mon Feb 15 12:29:28 2010 OPTIONS IMPORT: timers and/or timeouts modified
Mon Feb 15 12:29:28 2010 TUN/TAP device tap0 opened
Mon Feb 15 12:29:28 2010 TUN/TAP TX queue length set to 100
Mon Feb 15 12:29:28 2010 Initialization Sequence Completed
```but i can't see tap0 interface and cannot ping any address at remote location.

I tried this config file at Windows OpenVPN client and all works fine.

Could anyone help me?

Thx in advance.

---

### Post by bogdan.veringioiu on 2010-02-15
Hi.

After you see the message "Initialization Sequence Completed", open a new terminal (do not close the current one or hit Ctrl+c as you will interrupt the connection), and type ifconfig.
What is the output?
Bogdan

---

### Post by magul on 2010-02-15
Hi,

I have solved problem by myself.

Solution was adding to /etc/network/interfaces
```
auto tap0
iface tap0 inet dhcp
```and everytime when i try to connect, after ```
Mon Feb 15 16:28:44 2010 Initialization Sequence Completed
``` I need to reload networking using

```
sudo /etc/init.d/networking restart
```

(Note, that on Kubuntu I don't need to restart networking, but starting openvpn from console causes double crash of KDE)

---

