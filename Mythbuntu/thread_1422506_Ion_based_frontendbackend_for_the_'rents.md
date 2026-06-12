---
title: "Ion based frontend/backend for the 'rents"
date: 2010-03-05
forum: Mythbuntu
---

### Post by itlarson on 2010-03-05
I am considering building an ion based frontend/backend for my parents.  They are retired, and travel alot, and mythtv would allow them to export tv shows to files on their laptop for viewing away from home.  They only watch PBS over the air, so a single tuner will work.  Their only tv is a 26" flat panel,  so their is no need for a separate backend.  I am looking at an Asus ion board (see the link below) which has a dual core atom.  It has a pci slot which I would use for a pchdtv-5500 card, and three sata connectors which should be plenty, since I won't put an optical drive in this box.  Does anyone have any thoughts about this?  Lots of people use ion's for frontends, but this is the first combined ion system I have heard of.  But I don't see any reason why it wouldn't work.    

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131408&cm_re=ion_motherboard-_-13-131-408-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131408&cm_re=ion_motherboard-_-13-131-408-_-Product)

---

### Post by colinnwn on 2010-03-05
That is a sweet little system. Only thing I would prefer is a PCI-e slot rather than PCI. 

Backends with analog hardware encoding capture cards, or digital capture cards, require very little horsepower. Frontends require a lot of horsepower to display HD, unless you use VDPAU.

On this MB, it looks like you don't have the option to use a discrete video card, unless you get one of the few PCI vid cards, and then you would need an external capture device. But the fact the onboard NVIDIA GeForce 9400M supports VDPAU means you shouldn't need to use a discrete vid card.

I'd go for it.

---

### Post by timconradinc on 2010-03-05
I use mythexport to do something similar for my parents. It works pretty well. I imagine there is software people like better, but using iTunes to grab the podcast works pretty well. It can be set up to automatically download or only download specific episodes.

I suppose how well that works would depend if they had full-time internet at home or not. I have my router that connects to the internet update the IP using a free registration service, and they connect to that DNS name, so if my IP changes, it still works properly.

---

### Post by ZedThou on 2010-03-05
I've been running a combined FE/BE on an IONITX-A for a few months now, it works well for what it does. I don't do any transcoding at all, and have no idea how satisfactory the ION platform would perform in that capacity. It took some time to figure out just what X server options work best, but generally speaking you'll want at least 2GB memory so you can allocate 512 MB to the IGP. Sometimes the frontend crashes and I have to manually restart it. Not a big deal really, but be aware your parents may also need to do so from time to time.

---

### Post by colinnwn on 2010-03-05
> **ZedThou said:**
> Sometimes the frontend crashes and I have to manually restart it. Not a big deal really, but be aware your parents may also need to do so from time to time.

Should be easy enough to write a script that checks for the FE running every couple minutes, and if it isn't it relaunches the FE. Years ago when I was running KnoppMyth, MythTV had some kind of bug that would occasionally cause the BE to crash, and the KnoppMyth guys had a really nice script that relaunched the BE.

---

