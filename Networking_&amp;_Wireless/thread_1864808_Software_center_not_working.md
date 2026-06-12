---
title: "Software center not working"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by exwindowuser on 2011-10-19
lsb_release -a:

Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

Everytime i try 'sudo apt-get update' from the terminal, it gets stuck at 47%, trying to connect to (10.43.42.6). I think it's trying to connect to itself since i activated the loopback adapter with that address. I "ifconfig lo down" but it's still doing the same thing. Also when i try to download somtething, the Software center says "updating cache 0b of 1 b." IT gets stuck then doesn't go forward. 

need to download software. Any help is welcome. Thanks

---

### Post by e79 on 2011-10-19
> ...trying to connect to (10.43.42.6). I think it's trying to connect to itself since i activated the loopback adapter with that address.Curiously...why would you change the loopback adapter from its default 127.0.0.1 address ? IMHO, you should never-ever touch this value. Could you try putting it back to this value and apt-get update again ?

---

### Post by e79 on 2011-10-20
Mind to give feedback or reply perhaps ?

---

