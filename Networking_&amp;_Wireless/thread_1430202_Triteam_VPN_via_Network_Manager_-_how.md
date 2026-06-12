---
title: "Triteam VPN via Network Manager - how??"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by Thanh-BKK on 2010-03-15
Hello.

Is there any way to get a Triteam VPN connection going by using the connection manager? I am struggling with this....... 

It is using Open VPN, i have received the following files from them:

username.crt
username.key
username.ovpn
ca.crt
ta.key

And i have, frankly, no idea how to get it going. I also have a username and a password. As per their instructions i have to use the terminal to go into the folder with those files and start the connection with this command:

sudo openvpn --config username.ovpn

Doing so prompts for the username and the password and then runs an awful lot of text and then it connects, so it works.

However i have to disconnect and reconnect the VPN multiple times a day and i don't want to have an open terminal session running all the time.... hence i want to use the connection manager. 

But all i get so far is "Failed to connect because the connection attempt timed out". 

This is what is in the config file:

float

remote 76.73.107.106 80

dev tun

persist-key

persist-tun

proto udp

pull

route-method exe

route-delay 2

nobind

tun-mtu 1500

comp-lzo

auth-user-pass

auth RSA-RIPEMD160

cipher AES-256-CBC

tls-cipher DHE-RSA-AES256-SHA

tls-client

client

tls-auth ta.key 1

ns-cert-type server

ca ca.crt

cert username.crt

key username.key

keepalive 10 60

resolv-retry 86400

verb 1 

How can i get all of that stuff into the connection manager..?

I would highly appreciate some help in this matter.... many thanks in advance.

Kind regards.....

Thanh

---

### Post by Thanh-BKK on 2010-03-16
*bump*

I found out how to import the settings file (username.ovpn) in connection manager however problem persists - just differently.

Now connection manager, pretty much immediately after trying to connect, comes up with this:

"The VPN Connection 'Triteam' failed to connect because the VPN service failed to start"

I tried it with KVpnc and, no real surprise, this fails as well:

"TLS key negotiation failed to occur within 60 seconds"

Is it really THAT difficult to get Open VPN working on Jaunty??

Regards.....

Thanh

---

