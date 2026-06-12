---
title: "No ethernet connection or options"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by Markn951 on 2011-08-18
Hey all,

So, I've just installed Ubuntu 10.04 LTS. I've previously tried vanilla 11.04,and Xubuntu 11.04, and both worked fine with both my wired connection and my wireless card. I know on Windows, my motherboard's NIC needs a separate driver install, it doesn't work out of the box. Previous to the driver install it's as if there is no ethernet connection at all. My issue is that now that I'm using 10.04, basically the same thing is happening. Usually I'll have Auto eth0 and the Wireless option, but eth0 isn't being configured automatically. Can someone walk me through setting up my ethernet connection? I'm more comfortable setting it up through Terminal if possible. (ifconfig only gives me lo and wlan0, btw)

Thank you in advance!

---

### Post by gordintoronto on 2011-08-18
It sounds like your Ethernet adapter is not supported by the kernel in Ubuntu 10.04. The simple solution is to install 11.04.

If you really want to try to make it work, open Accessories/Terminal and enter the command: lspci

About 15 lines of output will be produced, and one of them will be your Ethernet Adapter. Post that line here. (Or the whole works, if you're not sure what line it is.)

---

### Post by Markn951 on 2011-09-04
Sorry it took so long to respond! I spent about a week and a half using the wireless card and then I decided I wanted to try Arch. Setting that up was fun, and interestingly enough, my ethernet adapter worked just fine, with no real setup on my part... This leads me to believe it IS a configuration issue, not an incompatibility/support issue. (I am coming back to 10.04 now, though. I like having everything set up for me automatically :) )

lspci tells me the ethernet controller is an Atheros 1083. Upon some google prodding, it does seem like it's a kernel support issue. Turns out they added support for this NIC in 2.6.38, whereas uname says I'm on 2.6.32. I'm going to see if I can upgrade the kernel somewhat easily...

Yes, I should be able to simply apt-get linux-image-x.x.xx-xx... I'll search to see if they have 2.6.38 available.

Yes, it's available! Didn't even need to configure repositories at all. Installing now...

That did it! eth0 is now working properly. Now all I need to do is apt-get remove linux-image-2.6.32-generic and I'm all set!

Hope this helps someone in the future :)

---

### Post by nm_geo on 2011-09-04
> **Markn951 said:**
> Sorry it took so long to respond! I spent about a week and a half using the wireless card and then I decided I wanted to try Arch. Setting that up was fun, and interestingly enough, my ethernet adapter worked just fine, with no real setup on my part... This leads me to believe it IS a configuration issue, not an incompatibility/support issue. (I am coming back to 10.04 now, though. I like having everything set up for me automatically :) )

lspci tells me the ethernet controller is an Atheros 1083. Upon some google prodding, it does seem like it's a kernel support issue. Turns out they added support for this NIC in 2.6.38, whereas uname says I'm on 2.6.32. I'm going to see if I can upgrade the kernel somewhat easily...

Yes, I should be able to simply apt-get linux-image-x.x.xx-xx... I'll search to see if they have 2.6.38 available.

Yes, it's available! Didn't even need to configure repositories at all. Installing now...

That did it! eth0 is now working properly. Now all I need to do is apt-get remove linux-image-2.6.32-generic and I'm all set!

Hope this helps someone in the future :)

Good job Markn.. and thanks for the information..
By the way drop the 

```
lspci -nn
```

and 

```
sudo lshw -C network 
```

result might help too

---

### Post by fdrake on 2011-09-04
can you try to do some updates , maybe they have a fix for your issue:
(make sure your repo are all enabled please:"backports" too)
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-image-$(uname -r)
sudo apt-get install --reinstall linux-backports-modules-wireless-$(less /etc/lsb-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f 2)-$(uname -r | cut -d "-" -f 3)
sudo aptitude update
sudo aptitude upgrade
sudo reboot 0 # this will reboot your machine

```

in case of errors post them (copy/paste)here

---

