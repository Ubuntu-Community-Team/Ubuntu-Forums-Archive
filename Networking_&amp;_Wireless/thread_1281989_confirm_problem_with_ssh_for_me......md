---
title: "confirm problem with ssh for me....."
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by linux000019 on 2009-10-03
everytime i start up limewire and ssh, the connection is aborted by software.
 
multiplayer gaming is working over the ssh connection; and it can stay connected for seemingly endless time amounts without disconnecting. as soon as i start a torrent or limewire though, that software abort error ends it.
 
is this normal?

---

### Post by SoftwareExplorer on 2009-10-04
Well, maybe the traffic the p2p is generating causing enough congestion to make the connection time out? What error message do you get exactly?

---

### Post by doas777 on 2009-10-04
> **linux000019 said:**
> everytime i start up limewire and ssh, the connection is aborted by software.
 
multiplayer gaming is working over the ssh connection; and it can stay connected for seemingly endless time amounts without disconnecting. as soon as i start a torrent or limewire though, that software abort error ends it.
 
is this normal?

my guess is that tunneling is not quite compatible with the way limewire handles connections (eg: it creates a ton of them). passing all of them through your tunnel port may cause some confusion in terms of syn sequences and whatnot.  just a guess though.

---

### Post by linux000019 on 2009-10-05
> **doas777 said:**
> my guess is that tunneling is not quite compatible with the way limewire handles connections (eg: it creates a ton of them). passing all of them through your tunnel port may cause some confusion in terms of syn sequences and whatnot.  just a guess though.


why does programs like yourfreedom.net or http-tunnel work then if i configure them for the ssh tunnel. also, firefox itself won't work through the tunnel; i set up the socks 5 tunnel on 1080 and for some reason multi-player gaming works but simpler things, like web browsing, aren't. although i admit that there is a internet filter on the computer running the ssh server and that could possibly be why firefox won't work. torrents and limewire work though on the ssh server, so http-tunnel and yourfreedom have computers running socks5 proxies that work with torrents and limewire i thought i could get mine too work like them.

the software error is:

"connection has been aborted by software." or "software caused connection to abort".

or something similar to that.

---

