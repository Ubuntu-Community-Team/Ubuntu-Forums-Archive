---
title: "Proxy denies access only on command line"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by ravi.xolve on 2010-03-25
I am behind a passworded proxy. I can connect to the Internet using  Firefox, Chrome or even Synaptic. But when I set the bash environment  variable as:
 	```

export http_proxy=http://user:password@proxy_address
```

and try to download the files using **wget** like bizip2 or  debian packages I get 404 error and with the pure domain names like [www.google.com]("http://www.google.com/") or [www.kde.org]("http://www.kde.org/") I just get the  default proxy password change page as output file.

What is the problem. I even tried changing the user-agent of wget or supplying the proxy user and password through its command options.

---

