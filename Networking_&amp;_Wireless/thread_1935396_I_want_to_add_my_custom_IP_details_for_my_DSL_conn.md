---
title: "I want to add my custom IP details for my DSL connection"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by bimaljr on 2012-03-04
Hello,

I am using Ubuntu 11.04 on my system.
I have internet connection which is based on PPPOE

I have configured it in DSL tab in "Network Connections" window. 
But my ISP provides me username, password, IP, Netmask and Gateway to connect internet.

I have added all details but the IP not applying and it's applying the dynamic IP (which given by server when login) and start to work.

I don't want to apply the IP which received when dialing but instead I want to use my own IP which provides by ISP.

So basically I want to override the IP which received when dialing DSL connection.

Please see attached screenshots:
1) Screenshot-Editing-Internet.png : This is the IP which I have added in DSL config box.
2) Screenshot-Connection Information.png : This is the Connection Information box and you can see different ip details than the IP I have inserted.

---

### Post by Phoenixxl on 2012-03-04
I don't have ubuntu desktop installed nor have I ever. I'm only familiar with ubuntu server. I expect both are the same in essence tbh.

You should have a file in /etc/ppp/peers named dsl-provider .

try adding 

10.20.44.66:
(or whatever your fixed ip is )

as the first option. don't forget the colon.

I've never used pppoe with a fixed address but according to the man page for pppd , the first option is local:remote ip , where either can be omitted.


OPTIONS
<local_IP_address>:<remote_IP_address>[INDENT]              Set  the local and/or remote interface IP addresses.  Either one
              may be omitted.  The IP addresses can be specified with  a  host
              name  or  in  decimal  dot  notation  (e.g. 150.234.56.78).  The
              default local address is the (first) IP address  of  the  system
              (unless  the  noipdefault  option is given).  The remote address
              will be obtained from the peer if not specified in  any  option.
              Thus,  in simple cases, this option is not required.  If a local
              and/or remote IP address is specified  with  this  option,  pppd
              will  not  accept  a  different  value from the peer in the IPCP
              negotiation,     unless     the     ipcp-accept-local     and/or
              ipcp-accept-remote options are given, respectively.
[/INDENT]



I haven't tried this myself , be sure to make a copy of your dsl-provider file before trying this. Just throwing a few ideas around. Fingers crossed.


EDIT: Or -> 10.20.44.66:10.20.0.1

---

