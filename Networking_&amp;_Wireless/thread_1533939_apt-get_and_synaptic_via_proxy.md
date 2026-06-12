---
title: "apt-get and synaptic via proxy"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2010-07-18
Hi,
I know that other people have had similar problems, but the various solutions posted elsewhere haven't helped me yet. 
10.04 and I are living behind a proxy that requires authentication. My system proxy is set properly as is the proxy setting in synaptic. Synaptic actually works without problem for downloading software.  But I can't add a PPA to my software sources without running into a 

```
<urlopen error Tunnel connection failed: 407 Proxy Authentication Required>
```

error. (I'm trying to fix the dreaded Intel i845 crash bug.)
I've tried 
```
sudo -i
export http_proxy=http://user: password@proxy: proxyport/
(I've added spaces after the : to avoid smilies)
```
but that hasn't helped. I've also ensured that my /etc/apt/apt.conf is properly configured. I've even tried doing it via the GUI by running 
```
sudo synaptic
```
without success.
The PPA's I'm trying to add are:
apt-add-repository ppa:glasen/855gm-fix  
apt-add-repository ppa:brian-rogers/graphics-fixes 
apt-add-repository ppa:glasen/intel-driver
Any ideas?
Thanks,

---

