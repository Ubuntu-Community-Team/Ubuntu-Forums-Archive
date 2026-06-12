---
title: "Google's 1e100.net domain and netstat with root"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by sloggerkhan on 2012-07-24
```

tcp        0      0 ----------------------------:37315 lax02s01-in-f16.1e100.net:https ESTABLISHED ------    784604      23669/firefox   
tcp        0      0 ----------------------------:52031 pz-in-f84.1e100.net:https ESTABLISHED ------    785435      23669/firefox   
tcp        0      0 ----------------------------:56035 lax02s01-in-f3.1e100.net:http TIME_WAIT   root       0           -               
tcp        0      0 ----------------------------:55875 lax02s01-in-f2.1e100.net:http TIME_WAIT   root       0           -               
tcp        0      0 ----------------------------:50657 lax02s01-in-f21.1e100.net:http ESTABLISHED ------    784698      23669/firefox   
tcp        0      0 ----------------------------:60457 lax02s01-in-f21.1e100.net:https ESTABLISHED ------    783202      23669/firefox   
tcp        0      0 ----------------------------:55722 pz-in-f95.1e100.net:http TIME_WAIT   root       0 
```

Why do the time wait connections to google's 1e100 domain show as coming from root?
(Used the command  ```
sudo netstat -t   -v -W -e -p -a | grep '1e100'
``` to generate above.)

They seem to stick around for a little bit after firefox closes.

Seems weird. Do all connections end up being managed by root at some level? Or is google doing something weird?

---

