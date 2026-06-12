---
title: "Notification reports connected to network, but it's lying"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by NautiusMaximus on 2013-05-28
I've been having great trouble getting my PC to connect up to my office network through a wired connection. I originally tried with DHCP. This was no end of trouble (and I wondered if it has something to do with an elderly and soon-to-be-retired Windows 2003 server which is running DHCP on the network, see [this]("http://ubuntuforums.org/showthread.php?t=2136043") thread), so I've now set it up as a static IP instead.

The network notification in the top right of the screen tells me, either at or shortly after boot-up, that I am connected to the network. If I type ifconfig at the terminal it gives the IP address that I thought I'd set for it.

However, it is not actually connected as far as I can tell. I can't visit websites, and I can't even ping anything on the same network.

Any idea what could be going wrong here? I'd be perfectly happy with either a DCHP connection or a static IP address. Anything that gets me onto the network is fine.

When I posted on the previous thread I was using Ubuntu 12.10, but have now upgraded to 13.04 in the vain hope that it might make things better.

Thanks
NM

---

### Post by NautiusMaximus on 2013-05-29
OK, I think I ***may*** have solved the problem. After a little more Googling and some further frigging about, I realised that it may be an issue with the driver for my ethernet adaptor. 

I have a Realtek RTL8111/8168 ethernet adaptor in my motherboard, and it turns out that there are some problems with the out-of-the-box Ubuntu driver for that adaptor. Happily, there seems to be a different adaptor that can be installed via the repositories that's been designed specifically for that adaptor and that should, in theory, solve some of the problems. Installing it was dead easy, with a single line at the terminal:

```
sudo apt-get install r8168-dkms
```

It seems to be working for now. I'm not marking this thread as solved just yet: I just want to make sure that it remains working consistently over the next few days.

Fingers crossed!

---

### Post by NautiusMaximus on 2013-06-18
Oh dear. It turns out that the problem wasn't solved at all. Oddly, it worked fine for a couple of days after I installed the updated driver, but now it's failing to connect again.

Any ideas?

---

