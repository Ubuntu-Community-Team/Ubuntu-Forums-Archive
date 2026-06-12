---
title: "Advice on setting up Dual Monitors"
date: 2011-01-31
forum: Multimedia Software
---

### Post by marshall1001 on 2011-01-31
I'm busy building a machine now and I'm looking to set up dual monitors because it's something I've always fancied but never had the resources to do.

I'm basically looking for advice on choosing a graphics card that will support dual monitors with good driver support under Ubuntu. After a few hours of browsing the forums I determined nVidia were the way to go but I'm honestly not bothered if people want to suggest ATI. I'm not a gamer so really only need the card to support dual monitors.

I'll also need to know how to set up the card under Ubuntu and then subsequently how to edit xorg.conf in order to get the dual monitors working.

Sorry to be such a dual-monitor noobie but I've never really had the chance to do it so haven't really looked into that much until now.

---

### Post by cascade9 on 2011-02-01
You shouldnt even have to edit xorg.conf to get dual monitors going with nvidia (or ATI/AMD as far as I know). 

Setting up dual monitors with nvidia x sever settings is pretty easy. ;)

Edit- do you know if you have a AGP/PCI system (old) or a motherboard with a PCIe slot?  Budget and location would probably help as well.

---

### Post by howefield on 2011-02-01
As cascade9 said, dual monitors are easily setup with nvidia cards. In my experience ATI slightly less so, but by no means difficult.

To set mine, I do the following.

In terminal type

```
sudo rm /etc/X11/xorg.conf
```

then 

```
gksudo nvidia-settings
```

Configure as Twinview (the two monitors act as one desktop) and set the position of the monitors in relation to each other and apply. (After applying if the panels are on the "wrong" monitor press the escape key and apply again) then save the configuration to /etc/X11/xorg.conf.

---

### Post by marshall1001 on 2011-02-06
> **cascade9 said:**
> You shouldnt even have to edit xorg.conf to get dual monitors going with nvidia (or ATI/AMD as far as I know). 

Setting up dual monitors with nvidia x sever settings is pretty easy. ;)

Edit- do you know if you have a AGP/PCI system (old) or a motherboard with a PCIe slot?  Budget and location would probably help as well.

I have a PCIe slot as I just bought the Motherboard a few weeks ago. My budget isn't tiny but neither is it infinite. Since I've never had to purchase a graphics card in the past I'm not sure what I'm really looking for in terms of price-range. I could stretch to about £100 for the graphics unit but I'm told that £50 - £60 should be more than enough for a dual-monitor set up since I'm not running games.

---

### Post by cascade9 on 2011-02-08
Even 50-60 quid is more than you would need for a nvida card with dual monitor support. 

An nvidia GT210 would be more than up to the job, and you can get them for under 30 quid. Then again, with your crazy VAT level and the way that most UK online shops I've seen quote 'ex-VAT' prices more like 35 quid in reality.

---

### Post by marshall1001 on 2011-02-09
> **cascade9 said:**
> Even 50-60 quid is more than you would need for a nvida card with dual monitor support. 

An nvidia GT210 would be more than up to the job, and you can get them for under 30 quid. Then again, with your crazy VAT level and the way that most UK online shops I've seen quote 'ex-VAT' prices more like 35 quid in reality.

Cheers

---

### Post by cascade9 on 2011-02-09
No problem. 

Good luck with whichever video card you get ;)

---

