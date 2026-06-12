---
title: "IPv6 - is it okay to enable it?"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by b9k9kiwi on 2011-12-23
Ubuntu 11.10

I disabled IPv6 in the previous version of Ubuntu in order to obviate Internet connection/traffic problems I was having (in common with other users and as suggested in this forum).

Time has passed and I am wondering if it is now okay (or worth) enabling IPv6 again.

---

### Post by Paddy Landau on 2011-12-23
Just try it. If it doesn't work, disable it again.

I once tried to enable IPv6 and had problems, but I don't remember which version of Ubuntu I was using at the time.

---

### Post by lisati on 2011-12-23
I haven't had the need to have IPv6 enabled everywhere on my machines yet. Like Paddy Landau, I've had problems in the past (can't remember which release) and disabled it, but haven't noticed any recent problems.

---

### Post by wildmanne39 on 2011-12-23
Hi, there are problems with some wireless cards where they will not connect or slow connections.
Thanks

---

### Post by b9k9kiwi on 2011-12-24
Thanks responders - I will leave IPv6 disabled for the time being.

---

### Post by owiknowi on 2012-01-07
@b9k9kiwi
could you please enlighten my 1-bit brain by explaining how you disable ipv6 system wide?
now i disable it only in firefox (about:config), but i also use another web browser.

thanks up front for any information!

p.s. using ubuntu 10.04.3 us -64

---

### Post by wildmanne39 on 2012-01-07
Hi, you can run this command:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
you can also set ipv6 to ignore in network manager please see screenshot.
Thanks

---

### Post by owiknowi on 2012-01-08
thanks wildmanne39! that will do the trick.

---

### Post by wildmanne39 on 2012-01-08
Hi, your welcome!

---

