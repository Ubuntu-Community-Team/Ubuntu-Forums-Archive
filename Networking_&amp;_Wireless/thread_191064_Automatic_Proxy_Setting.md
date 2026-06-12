---
title: "Automatic Proxy Setting"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by t0mc4t on 2006-06-07
My university using automatic proxy script to access its network.
How do I configure ubuntu to work with it? I have configured firefox successfuly, but I don't know how to configure the system. For example for synaptic to access the update, lynx (text browser), and GAIM, etc...
I have tried to put the script on Network Proxy from System Preferences on GNome but it didn't work.
Thanks...

---

### Post by SynapseR on 2006-06-08
Try this :

```
sudo gedit /etc/bash.bashrc
```

Add at end of file :

```
export http_proxy=http://proxyname:port
export ftp_proxy=http://proxname:port
```

Also, you can specify proxy settings in Synaptic under 
Settings -> Preferences > Network.

---

