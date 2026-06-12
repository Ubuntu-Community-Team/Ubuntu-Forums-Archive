---
title: "Using APT and Synaptic behind a proxy"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by alexlafreniere on 2009-08-13
On a previous installation of Xubuntu I had properly configured my apt.conf to work behind the proxy at my work. I tried to do this again after a fresh install but it only half works. After doing a sudo apt-get install command, apt properly downloads package information and begins to download the package but never gets past 0%. Also editing my bash.rc has never worked for me, but editing apt.conf has.Here is my apt.conf, with proxy info removed for obvious reasons:

```
APT {
Acquire {
http://myproxy.com:port;
};
}
```

Any help with this issue would be greatly appreciated.

---

### Post by alexlafreniere on 2009-08-13
Just a quick addition. I can install updates via the Update Manager, and I can download package information via the command line and in Synaptic, however I cannot actually download package from either of those sources.

---

