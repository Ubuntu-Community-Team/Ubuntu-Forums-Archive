---
title: "Open VPN question"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by MoebusNet on 2010-07-18
I used Shannon's script from [http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html](http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html) to tether my HTC Incredible phone to my notebook to be able to get on-line. It works wonderfully, but I have a question.

When I run the tethering script, I get the following in Terminal:

[sudo] password for glenn: 
adb: no process killed
openvpn: no process killed
* daemon not running. starting it now *
* daemon started successfully *
Sun Jul 18 13:40:45 2010 OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on May  8 2009
Sun Jul 18 13:40:45 2010 WARNING: --ping should normally be used with --ping-restart or --ping-exit
Sun Jul 18 13:40:45 2010 ******* WARNING *******: all encryption and authentication features disabled -- all data will be tunnelled as cleartext
Sun Jul 18 13:40:45 2010 TUN/TAP device tun0 opened
Sun Jul 18 13:40:45 2010 ifconfig tun0 192.168.56.2 pointopoint 192.168.56.1 mtu 1500
Sun Jul 18 13:40:45 2010 Attempting to establish TCP connection with 127.0.0.1:41927 [nonblock]
Sun Jul 18 13:40:45 2010 TCP connection established with 127.0.0.1:41927
Sun Jul 18 13:40:45 2010 TCPv4_CLIENT link local: [undef]
Sun Jul 18 13:40:45 2010 TCPv4_CLIENT link remote: 127.0.0.1:41927
Sun Jul 18 13:40:55 2010 Peer Connection Initiated with 127.0.0.1:41927
Sun Jul 18 13:40:55 2010 Initialization Sequence Completed

My question is about the ***WARNING*** ; are the encryption and authentication features disabled only from my notebook to the phone? 
Or have I completely disabled all that so that I can't use financial websites etc. now?

I am not conversant with OpenVPN, so any advice would be appreciated.

---

