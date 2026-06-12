---
title: "Port forwarding problem"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by false_chicken on 2010-12-02
I dont know if this is the proper place for this but it seems the most appropriate. I am trying to get transmissions webui ports to forward so I can check my  torrents on my phone while im on the go but I cannot get them to  forward. I have metrocast and have a sb5101 surfboard modem and a  buffalo whr-hp-g300n router running ddwrt. I have tried with all six  computers in my house. All running windows xp, 7 and ubuntu. Nothing can  go though and I dont know why. I am pretty sure I am doing this right  as it lets my xbox through. I goto NAT/QoS and give it a name, enter  port from and to as the same port, put down both for udp and tcp and  check the enabled box then I save and click apply. I even restarted the  router and modem several times and I have no firewalls running on any  system. Any suggestions? This is what I am using to check my ports:

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

---

### Post by puppywhacker on 2010-12-03
thanks for the yougotsignal like, I like it

I don't know if you tested webui already locally and if the port is listening to all the interfaces.

```
sudo apt-get install transmission-cli
transmission-daemon

```

if on transmission machine try to access the GUI using a URL like [http://192.168.1.1:9091/](http://192.168.1.1:9091/) using your internal ip-address and not localhost.

```
netstat -na | grep 9091
```

The point is that port 9091 (only TCP needed) should be open to all ip addresses and not just the localhost.

---

