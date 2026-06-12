---
title: "openvpn tls error"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by Jive Turkey on 2010-03-04
I'm very close, I think to getting this working. there is likely something missing from the wiki tutorial here [https://help.ubuntu.com/community/OpenVPN]("https://help.ubuntu.com/community/OpenVPN") but there is no way for me to know what it is.

I suspect it may be one of two things
A) wrong file permissions on one, some or all of the various certs on the client or server side.

B) Some undocumented procedure having to do with importing or signing the keys on the client side that everyone magically knows except for me.

Of course there is also the possibility that canonical forgot to disable the up-yours-jive-turkey option when building the openvpn package, but I doubt that.

Can anyone shed some light on this for me?

What are appropriate permissions on the keys?

Do you need to sign or import them on the client side, apart from pointing the client config to the path of the keys?  Who should own them?

What is missing from the above linked tutorial?

Here is an excerpt of the server side output that appears when I try to connect:```

 Data Channel MTU parms [ L:1590 D:1450 EF:58 EB:135 ET:32 EL:0 AF:3/1 
 Local Options hash (VER=V4): 'nnnnnnnn'
 Expected Remote Options hash (VER=V4): 'nnnnnnnn'
 TLS: Initial packet from x.x.x.x:xxxx, sid=nnnnnnn nnnnnnnn
 VERIFY ERROR: depth=0, error=unable to get local issuer certificate: /C=XX/ST=XX/L=XXXX/O=sXXX/CN=XXX/name=XX/emailAddress=XX@XX.com
 TLS_ERROR: BIO read tls_read_plaintext error: error:140890B2:SSL routines:SSL3_GET_CLIENT_CERTIFICATE:no certificate returned
 TLS Error: TLS object -> incoming plaintext read error
 TLS Error: TLS handshake failed
 SIGUSR1[soft,tls-error] received, client-instance restarting
```
So if you guys can help me get this going and its not PEBKAC I promise to fix the wiki howto for everyone.

Ultimately what I am after is the "road warrior" setup for tunneling through from public wifi (in addition to LAN access) if anyone has any tips for that.

Should I have to add an interface on the client /etc/networking/interfaces?

TIA

---

### Post by DGortze380 on 2010-03-04
Try rebuilding your certs.

---

