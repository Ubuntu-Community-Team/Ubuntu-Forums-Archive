---
title: "3G Internet Sharing"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by JoshHendo on 2009-01-08
Hi Everyone,

I am just wondering, how easy is it to have a laptop on a network and have it sharing an internet connection  (in this case, a 3G connection) with other computers on the lan (computer obviously Ubuntu, but other computers may be Windows or Ubuntu).

I have found a few things like:
[http://www.linuxforums.org/forum/ubuntu-help/103268-internet-connection-sharing-ubuntu-winxp.html](http://www.linuxforums.org/forum/ubuntu-help/103268-internet-connection-sharing-ubuntu-winxp.html)
and
[http://ubuntuforums.org/archive/index.php/t-742530.html](http://ubuntuforums.org/archive/index.php/t-742530.html)

But I want to know what is the best way. Is there a way I can just put my computer on the network (with a DHCP ip) and share the connection, or does my computer have to be plugged into the routers WAN port (I heard that somewhere, but wasn't sure about it -> I tried it and it won't connect, if I do need to do this, is there anyway I can).

It isn't essential, but it would be handy if there is a simple straight forward way to do this.

If this info is needed (I don't think it would be), but the card is a huawai e169 and works great with network manager)

Any help is appreciated.

---

### Post by dmizer on 2009-01-08
Try the following howto: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Your 3g device probably appears as ppp0. You can check the output of ifconfig to tell for sure. Here's mine for comparison:
```
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:xxx.xxx.xxx.xxx  P-t-P:xxx.xxx.xxx.xxx  Mask:xxx.xxx.xxx.xxx
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64 (64.0 B)  TX bytes:97 (97.0 B)
```

So, in the above howto, enter ppp0 where it says eth0, and you should end up with working ICS.

---

