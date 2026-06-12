---
title: "packageinstall behind proxy"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by eyvbog on 2009-11-04
Hi. Experiencing a strange problem; started using a public library wireless network a while ago, and now I can't seem to get updates and install any new packages. I have got all the proxy settings right, and can browse the internet just fine. Also, downloading files with ktorrent etc. merits no problems at all. But using kpackagekit, aptitude etc doesn't work at all. Recently made a clean install of 9.10 from 9.04, but had the same problem in jauntu. I can post output of code if that helps. Help will be greatly appreciated.

Eyvind

---

### Post by mister_doctor on 2009-11-04
Is the proxy information entered into ~/.bash_profile?

```

http_proxy="http://proxy.addr:port"
ftp_proxy="http://proxy.addr:port"

export http_proxy
export ftp_proxy

```

if the proxy uses some kind of authentication, that complicates things....

---

