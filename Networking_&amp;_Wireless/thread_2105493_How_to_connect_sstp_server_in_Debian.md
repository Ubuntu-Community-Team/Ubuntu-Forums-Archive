---
title: "How to connect sstp server in Debian?"
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by dxq38 on 2013-01-16
I compiled sstp-client(sstp-client.sourceforge.net/) in Debian.
And connect to a sstp server, i think connect success,
but my IP is the same as before.Why?Should I add route??
Thanks!!

**First i use sudo pon dsl-provider to connect internet.**
**then**
sudo plog
Jan 15 22:38:55 dong pppd[4279]: Connected to 00:04:23:ac:0b:3a via interface eth0
Jan 15 22:38:55 dong pppd[4279]: Starting negotiation on eth0
Jan 15 22:38:58 dong pppd[4279]: CHAP authentication succeeded
Jan 15 22:38:58 dong pppd[4279]: CHAP authentication succeeded
Jan 15 22:38:58 dong pppd[4279]: peer from calling number 00:04:23:AC:0B:3A authorized
Jan 15 22:38:58 dong pppd[4279]: Using interface ppp0
Jan 15 22:38:58 dong pppd[4279]: local IP address 10.10.0.224
Jan 15 22:38:58 dong pppd[4279]: remote IP address 10.10.0.1
Jan 15 22:38:58 dong pppd[4279]: primary DNS address 202.96.128.86
Jan 15 22:38:58 dong pppd[4279]: secondary DNS address 202.96.134.133


**After that, use sudo pon sstp-1**
**the log is:**
Jan 15 22:08:42 dong pppd[4087]: Plugin sstp-pppd-plugin.so loaded.
Jan 15 22:08:42 dong pppd[4088]: pppd 2.4.5 started by root, uid 0
Jan 15 22:08:42 dong pppd[4088]: using channel 2
Jan 15 22:08:42 dong pppd[4088]: Using interface ppp1
Jan 15 22:08:42 dong pppd[4088]: Connect: ppp1 <--> /dev/pts/2
Jan 15 22:08:42 dong sstpc[4092]: Waiting for sstp-plugin to connect on: /var/run/sstpc/sstpc-sstp-1
Jan  15 22:08:43 dong pppd[4088]: sent [LCP ConfReq id=0x1 <asyncmap  0x0> <magic 0xb13fab11> <pcomp> <accomp>]
Jan 15  22:08:46 dong pppd[4088]: sent [LCP ConfReq id=0x1 <asyncmap 0x0>  <magic 0xb13fab11> <pcomp> <accomp>]
Jan 15 22:08:47 dong sstpc[4092]: Resolved sstpv1.avpn.us to 50.117.117.234
Jan 15 22:08:47 dong sstpc[4092]: Connected to sstpv1.avpn.us
Jan 15 22:08:48 dong sstpc[4092]: Sending Connect-Request Message
Jan 15 22:08:48 dong sstpc[4092]: SSTP CRTL PKT(14)
Jan 15 22:08:48 dong sstpc[4092]: TYPE(1): CONNECT REQUEST, ATTR(1):
Jan 15 22:08:48 dong sstpc[4092]: ENCAP PROTO(1): 6
Jan 15 22:08:48 dong sstpc[4092]: SSTP CRTL PKT(48)
Jan 15 22:08:48 dong sstpc[4092]: TYPE(2): CONNECT ACK, ATTR(1):
Jan 15 22:08:48 dong sstpc[4092]: CRYPTO BIND REQ(4): 40
Jan 15 22:08:48 dong sstpc[4092]: Started PPP Link Negotiation
Jan 15 22:08:48 dong sstpc[4092]: SSTP DATA PKT(28)
Jan 15 22:08:48 dong sstpc[4092]: SSTP DATA PKT(28)
Jan 15 22:08:48 dong sstpc[4092]: SSTP DATA PKT(23)
Jan 15 22:08:48 dong pppd[4088]: rcvd [LCP ConfReq id=0x1 <auth chap MS-v2> <magic 0x8fe67404>]
Jan 15 22:08:48 dong pppd[4088]: sent [LCP ConfAck id=0x1 <auth chap MS-v2> <magic 0x8fe67404>]
Jan 15 22:08:48 dong sstpc[4092]: SSTP DATA PKT(23)
Jan 15 22:08:48 dong sstpc[4092]: SSTP DATA PKT(22)
Jan 15 22:08:48 dong pppd[4088]: rcvd [LCP ConfRej id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
Jan 15 22:08:48 dong pppd[4088]: sent [LCP ConfReq id=0x2 <magic 0xb13fab11>]
Jan 15 22:08:48 dong sstpc[4092]: SSTP DATA PKT(18)
Jan 15 22:08:48 dong sstpc[4092]: SSTP DATA PKT(22)
Jan 15 22:08:48 dong pppd[4088]: rcvd [LCP ConfRej id=0x1 <asyncmap 0x0> <pcomp> <accomp>]
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(18)
Jan 15 22:08:49 dong pppd[4088]: rcvd [LCP ConfAck id=0x2 <magic 0xb13fab11>]
Jan 15 22:08:49 dong pppd[4088]: sent [LCP EchoReq id=0x0 magic=0xb13fab11]
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(16)
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(37)
Jan 15 22:08:49 dong pppd[4088]: rcvd [CHAP Challenge id=0x1 <db0d770ce73d88ca4549fe097f923741>, name = "MikroTik"]
Jan  15 22:08:49 dong pppd[4088]: sent [CHAP Response id=0x1  <65a60fcd6b6cf039783fec0b2c0f490f0000000000000000f7af16081e146d18b1a878c10365c0d761b8466165e7a1fe00>  , name = "dxq83"]
Jan 15 22:08:49 dong pppd[4088]: sstp_snoop_send: mppe keys are set
Jan 15 22:08:49 dong pppd[4088]: sstp_snoop_send: The mppe send key: 18c80dacd4a656ba1f4be3c3fcee52e4
Jan 15 22:08:49 dong pppd[4088]: sstp_snoop_send: The mppe recv key: ecdfe5d6499288092c45532fa35def5a
Jan 15 22:08:49 dong sstpc[4092]: Received callback from sstp-plugin
Jan 15 22:08:49 dong sstpc[4092]: Sending Connected Message
Jan 15 22:08:49 dong sstpc[4092]: SSTP CRTL PKT(112)
Jan 15 22:08:49 dong sstpc[4092]: TYPE(4): CONNECTED, ATTR(1):
Jan 15 22:08:49 dong sstpc[4092]: CRYPTO BIND(3): 104
Jan 15 22:08:49 dong sstpc[4092]: Connection Established
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(67)
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(16)
Jan 15 22:08:49 dong pppd[4088]: rcvd [LCP EchoRep id=0x0 magic=0x8fe67404]
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(54)
Jan 15 22:08:49 dong pppd[4088]: rcvd [CHAP Success id=0x1 "S=E34D68389B28AD64EDAE2D019B963587507E0EF0"]
Jan 15 22:08:49 dong pppd[4088]: CHAP authentication succeeded
Jan  15 22:08:49 dong pppd[4088]: sent [IPCP ConfReq id=0x1 <compress VJ  0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2  0.0.0.0>]
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(36)
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(18)
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(22)
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(12)
Jan 15 22:08:49 dong pppd[4088]: rcvd [IPCP ConfReq id=0x1 <addr 69.195.128.12>]
Jan 15 22:08:49 dong pppd[4088]: sent [IPCP ConfAck id=0x1 <addr 69.195.128.12>]
Jan 15 22:08:49 dong pppd[4088]: rcvd [IPV6CP ConfReq id=0x1 <addr fe80::0000:0000:0000:0077>]
Jan 15 22:08:49 dong pppd[4088]: Unsupported protocol 'IPv6 Control Protocol' (0x8057) received
Jan 15 22:08:49 dong pppd[4088]: sent [LCP ProtRej id=0x3 80 57 01 01 00 0e 01 0a 00 00 00 00 00 00 00 77]
Jan 15 22:08:49 dong pppd[4088]: rcvd [proto=0x8281] 01 01 00 04
Jan 15 22:08:49 dong pppd[4088]: Unsupported protocol 'MPLSCP' (0x8281) received
Jan 15 22:08:49 dong pppd[4088]: sent [LCP ProtRej id=0x4 82 81 01 01 00 04]
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(18)
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(28)
Jan 15 22:08:49 dong sstpc[4092]: SSTP DATA PKT(18)
Jan 15 22:08:50 dong sstpc[4092]: SSTP DATA PKT(18)
Jan 15 22:08:50 dong pppd[4088]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
Jan 15 22:08:50 dong pppd[4088]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jan 15 22:08:50 dong sstpc[4092]: SSTP DATA PKT(30)
Jan 15 22:08:50 dong sstpc[4092]: SSTP DATA PKT(30)
Jan  15 22:08:50 dong pppd[4088]: rcvd [IPCP ConfNak id=0x2 <addr  10.3.3.204> <ms-dns1 208.67.222.222> <ms-dns2  208.67.220.220>]
Jan 15 22:08:50 dong pppd[4088]: sent [IPCP  ConfReq id=0x3 <addr 10.3.3.204> <ms-dns1 208.67.222.222>  <ms-dns2 208.67.220.220>]
Jan 15 22:08:50 dong sstpc[4092]: SSTP DATA PKT(30)
Jan 15 22:08:50 dong sstpc[4092]: SSTP DATA PKT(30)
Jan  15 22:08:50 dong pppd[4088]: rcvd [IPCP ConfAck id=0x3 <addr  10.3.3.204> <ms-dns1 208.67.222.222> <ms-dns2  208.67.220.220>]
Jan 15 22:08:50 dong pppd[4088]: local IP address 10.3.3.204
Jan 15 22:08:50 dong pppd[4088]: remote IP address 69.195.128.12
Jan 15 22:08:50 dong pppd[4088]: primary DNS address 208.67.222.222
Jan 15 22:08:50 dong pppd[4088]: secondary DNS address 208.67.220.220
Jan 15 22:08:50 dong pppd[4088]: Script /etc/ppp/ip-up started (pid 4097)
Jan 15 22:08:51 dong ntpd[2751]: Listen normally on 6 ppp1 10.3.3.204 UDP 123
Jan 15 22:08:51 dong ntpd[2751]: peers refreshed
Jan 15 22:09:00 dong pppd[4088]: Script /etc/ppp/ip-up finished (pid 4097), status = 0x0
Jan 15 22:09:19 dong sstpc[4092]: SSTP DATA PKT(16)
Jan 15 22:09:19 dong sstpc[4092]: SSTP DATA PKT(16)

---

### Post by jonobr on 2013-01-16
Not sure of sstp but Im thinking if you do a nslookup on eg cnn.com
check which dns respnds to the request.

Then created the secure tunnel and then do another nslookup,
see if its the same.

If its not , you going through the tunnel.

Also, traceroute should show the same thing,
traceroute to a remote host disconnected, then connect and see if you get the same response.

---

### Post by dxq38 on 2013-01-16
> **jonobr said:**
> Not sure of sstp but Im thinking if you do a nslookup on eg cnn.com
check which dns respnds to the request.

Then created the secure tunnel and then do another nslookup,
see if its the same.

If its not , you going through the tunnel.

Also, traceroute should show the same thing,
traceroute to a remote host disconnected, then connect and see if you get the same response.
Thanks so much!
I'll try it!:p

---

### Post by dxq38 on 2013-01-16
> **jonobr said:**
> Not sure of sstp but Im thinking if you do a nslookup on eg cnn.com
check which dns respnds to the request.

Then created the secure tunnel and then do another nslookup,
see if its the same.

If its not , you going through the tunnel.

Also, traceroute should show the same thing,
traceroute to a remote host disconnected, then connect and see if you get the same response.

Before connect SSTP:
nslookup cnn.com                 
Server:         8.8.8.8                                                                    
Address:        8.8.8.8#53                                                                 
                                                                                           
Non-authoritative answer:                                                                  
Name:   cnn.com                                                                            
Address: 157.166.226.25                                                                    
Name:   cnn.com                                                                            
Address: 157.166.226.26                                                                    
Name:   cnn.com                                                                            
Address: 157.166.255.18                                                                   
Name:   cnn.com                                                                            
Address: 157.166.255.19

After connected SSTP:
nslookup cnn.com                
Server:         208.67.222.222                                                             
Address:        208.67.222.222#53                                                          
                                                                                           
Non-authoritative answer:                                                                  
Name:   cnn.com                                                                            
Address: 157.166.226.26                                                                    
Name:   cnn.com                                                                            
Address: 157.166.255.18                                                                    
Name:   cnn.com                                                                            
Address: 157.166.255.19                                                                    
Name:   cnn.com                                                                            
Address: 157.166.226.25     

Looks like the DNS has changed. But still i can not open twitter,facebook,youtube. And my IP is the same as before.I don't know why.
You know there is GFW(Great Fire Wall) in China.:p

---

### Post by dxq38 on 2013-01-18
Finally, solved.
[http://sstp-client.sourceforge.net/](http://sstp-client.sourceforge.net/)
sstp-client compile

sudo apt-get install ppp-dev
sudo apt-get install libevent-dev
sudo apt-get install libssl-dev

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --includedir=/usr/include --libexecdir=/usr/lib/sstp-client --mandir=/usr/share/man --infodir=/usr/share/info --disable-dependency-tracking --with-runtime-dir=/var/run/sstpc --enable-user --enable-group
make
sudo make install

make a dir : sudo mkdir /var/run/sstpc

/etc/ppp/chap-secrets file contents&#65306;
# Secrets for authentication using CHAP
# client server secret IP addresses
username sstp-1 "password" *

/etc/ppp/peers/sstp-1 file contents:
remotename      sstp-1
linkname        sstp-1
ipparam         sstp-1
pty             "sstpc --ipparam sstp-1 --log-level 4 --save-server-route --nolaunchpppd your_server"
name            username
plugin          sstp-pppd-plugin.so
sstp-sock       /var/run/sstpc/sstpc-sstp-1
usepeerdns
#require-mppe
refuse-eap
noauth
debug
defaultroute


sudo pon sstp-1

---

