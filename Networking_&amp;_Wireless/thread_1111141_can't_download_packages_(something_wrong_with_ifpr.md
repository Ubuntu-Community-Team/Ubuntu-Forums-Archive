---
title: "can't download packages (something wrong with ifproxy)"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by Kerato on 2009-03-30
when i try to install soma applications i get this message for every package:

W: Failed to fetch [http://ubuntu.tiscali.nl/pool/universe/p/p7zip/p7zip-full_4.58~dfsg.1-1_i386.deb](http://ubuntu.tiscali.nl/pool/universe/p/p7zip/p7zip-full_4.58~dfsg.1-1_i386.deb)
  Could not resolve 'ifproxy'

my internet works properly

---

### Post by BkkBonanza on 2009-03-30
Are you using Aptitude or Synaptic to install?

Synaptic you can configure the proxy from it's menu Settings, preferences, Network

but Aptitude uses environment variables.

To see what environment variables are in effect type,

env | grep proxy

It should only show lines related to proxy settings. If there is a proxy set there you would likely want to change it in one of the console init scripts like profile or bashrc.

---

### Post by Kerato on 2009-03-31
```
kees@kees-laptop:~$ env | grep proxy
http_proxy=http://ifproxy:3128/
```

and now? I just want a direct internet connection. please help.

---

### Post by BkkBonanza on 2009-03-31
You can remove that environment variable with,

export http_proxy=

But it may come back if it's in a startup file. So you will want to check these files,

/etc/profile
/etc/bashrc
~/.profile
~/.bashrc

If you see a line like "export http_proxy=something" then remove it and save the file. That line is setting up your environment with a proxy.

---

