---
title: "VPN Server Setup"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by mikeym on 2009-09-29
Hi,

I'm trying to set up a VPN server. I've got a few questions about VPN to begin with (and I've read everything I can find on it but I've not found the answer - at least not so that I could understand):

[SIZE="4"]A Few Qestions About VPN[/SIZE]

[LIST]
[*]Can one VPN client see another VPN client on the nework?

[*]If it can does all traffic between them have to go through the server?

[*]Can you use a VPN as a mini internet with web hosting, chat and games servers?
[/LIST]

So now that I've asked that I'd also like to ask a few things about setting up a VPN server because I've tried every guide I can find to no evail.

[SIZE="4"]Setting Up A VPN Server[/SIZE] 

The [Ubuntu Community guide]("https://help.ubuntu.com/community/OpenVPN") tries to set up bridging first which I have been unable to do. My rooter assigns me an IP through DHCP which is tied to the MAC address of the card to always be the same, but I can't find out how to set up my */etc/network/interfaces* file for this. 

I tried working through it without a bridge but when creating the keys I get:

```
$ ./build-dh
Generating DH parameters, 2048 bit long safe prime, generator 2
This is going to take a long time
.+.................................................+..............................................++*++*
unable to write 'random state'

```

I've tried making the keys using the [video guide and gnomint]("http://www.youtube.com/watch?v=KbInXaFbC8g") and finishing the ubuntu guide from there. 

However when I try an connect using the following client.conf file from my gentoo computer

```
client
dev tun
proto tcp
# change this to your servers ip or hostname 
 
remote nixon 11194
resolv-retry infinite
nobind

persist-key
persist-tun

ca /home/mikey/.havenvpn/havenvpnca.crt
cert /home/mikey/.havenvpn/client1.crt
key /home/mikey/.havenvpn/client1.key

comp-lzo
verb 3
```

I get:

```
Tue Sep 29 22:19:34 2009 OpenVPN 2.1_rc15 powerpc-unknown-linux-gnu [SSL] [LZO2] [EPOLL] built on Sep 29 2009
Tue Sep 29 22:19:34 2009 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Tue Sep 29 22:19:34 2009 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Tue Sep 29 22:19:34 2009 Cannot load private key file /home/mikey/.havenvpn/client1.key: error:0906D06C:PEM routines:PEM_read_bio:no start line: error:140B0009:SSL routines:SSL_CTX_use_PrivateKey_file:PEM lib
Tue Sep 29 22:19:34 2009 Error: private key password verification failed
Tue Sep 29 22:19:34 2009 Exiting

```

Could someone please help 'cos I'm not getting anywhere quickly?

---

### Post by mattkoehn on 2009-09-29
So openvpn right? Going forth assuming that...

1. You can set whether you want clients to be able to see each other in the server conf file.

2. Yes.

3. Yes. But mind the ways you have your clients connecting as you will experience slowdowns with compression or tighter security. But depending on what way you have your web services running on your server, whatever you run on your server will show up to your clients or at least can unless you change it.


As for your connection issue. DH doesn't really matter for connection purposes. Unless you plan to use it. I never have. It is for securely sharing keys with a client over the internet. (Actually you aren't sharing them you are connecting to a client and creating the key file at the two locations without it being transferred.) So if you just want to connect, ignore that for now.

Make sure that you actually have you key file in that location and the correct case. Try creating new keys using the website [http://www.openvpn.net/howto](http://www.openvpn.net/howto) . 

That error doesn't look familiar to me, which makes me think it could be a key issue. Creating new keys should only take you 5min. 

Good luck.

---

### Post by Natanael on 2012-05-19
I've got the same error as above when trying to start client. Have you solved the problem? Can anyone help?

---

