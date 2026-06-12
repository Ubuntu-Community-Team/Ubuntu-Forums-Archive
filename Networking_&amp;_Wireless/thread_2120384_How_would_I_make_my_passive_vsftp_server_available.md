---
title: "How would I make my passive vsftp server available via internal &amp; external network?"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by beejee on 2013-02-26
Heya,

I have a vsftp setup to accept passive ftp connections, these originate from some closed logger devices that only do passive ftp, so no change of config is possible on the little critters. 
My machines are behind a nat so vsftpd replies to an ftp request with the internal address (192.168.*.*), which can be easily fixed by adding following line to /etc/vsftpd.conf: 

```
pasv_address= xx.xx.xx.xx
```



So far so good, but I now have one of these boxes inside my network, once it starts uploading it's data via ftp it connects to the internal address (192.168.*.*) but receives  the external address from the ftp server.

Does anyone know a way to have vsftp differentiate between different networks or another workaround for this?


Thanks!

---

