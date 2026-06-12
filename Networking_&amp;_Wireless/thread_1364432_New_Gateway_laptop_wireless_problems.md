---
title: "New Gateway laptop wireless problems"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by RedClairefield on 2009-12-25
I'm running Linux Mint 8 which is more or less the latest version of Ubuntu

It's my christmas present, obviously, and it's a Gateway. It came with Windows 7, but I installed Mint 8 on a new partition because I honestly despise Windows 7 and was having more trouble with it than I needed to.

Now I'm having trouble with Ubuntu. It found all my drivers, but the wireless is kind of wonky. If I download much of anything from firefox, the connection drops and I can't reconnect. I can't log out and back in, because if I log out it goes to the shell for some reason. So I've had to restart my computer several times because I wanted to download a game from sourceforge.

When I looked at the specs in Windows 7, it said the laptop was in the NV52 series
[http://support.gateway.com/s/notebook/2009/gateway/nv/nv52/NV52sp2.shtml](http://support.gateway.com/s/notebook/2009/gateway/nv/nv52/NV52sp2.shtml)

But the bottom of the computer said the model is MS2274

I don't know any of the driver names or how to find them out.

Not sure what any of this means. I'd like some help though, because I like christmas presents that work.

---

### Post by gordintoronto on 2009-12-25
If you connect to the router, you probably have the right driver.  How is the signal strength?  I really don't have a helpful suggestion.

---

### Post by Aaardwark on 2010-01-11
It's a problem with the atheros driver, install the backports.

```
sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```

---

