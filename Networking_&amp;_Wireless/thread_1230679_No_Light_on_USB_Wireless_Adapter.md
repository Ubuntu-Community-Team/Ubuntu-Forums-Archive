---
title: "No Light on USB Wireless Adapter"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by TeeSee62 on 2009-08-03
Hi All,
my very first post of many; more than likely. 
Just installed my first non MS OS this weekend (Jaunty) and after a few false starts 3rd time lucky am now running it as primary OS on dual boot with XP for my games. What I can see of it so far I really like!
Anyway, it's not really a question but it's just that I'm curious. I have a sitecom wireless router with a Sitecom WL535 USB adapter.
After installing Jaunty I've had absolutely no problem connecting to net using the generic system (in other words I have no clue how it connected but it did straight off! - so I'm one of the lucky ones!).
The only thing is that when I boot into windows the USB adapter lights up - and also the signal strength indicator says 'Excellent'
In Jaunty however the adapter stays unlit and the network manager reports around 15% connectivity. Also I've noticed that it seems a little sluggish sometimes when using the browser i.e. pages take longer to load. 
I've looked on Sitecom's drivers page but I cant really make head or tail of whether I need to install a Linux driver for it. Still, I have a connection am I reading too much into this?
TIA

---

### Post by quixote on 2009-08-04
Windows is probably setting some flag in the system that Linux then uses, except you'd really rather it didn't!

That said, I don't know how you'd fix it.  Somehow, the system needs to be kicked to clear that information.  If the wireless card is external, can you tell Windows to unmount that USB device before you quit Windows?  Or maybe restart network services in Linux? ```
sudo /etc/init.d/networking restart
```

I'm just guessing. :(

---

