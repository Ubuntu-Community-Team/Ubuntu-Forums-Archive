---
title: "Nvidia GeForce2 GTS/Pro"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by ksonic1055 on 2007-12-16
My device manager in ubuntu 7.10 indicates that my graphics card is a NV15 [GeForce2 GTS/Pro]. Im not sure there is a driver installed for this device because under the device tab i see: Device type: Unknown  and   Device capabilities: Unknown.

Also, screensavers such as Euphoria are very slow and skip many frames. 

Where can I get a decent driver for my card?



thanks

---

### Post by ksonic1055 on 2007-12-16
ok well I found a driver using add/remove programs. I installed it and now i have a perfectly working graphics card, except now the resolution is really low, and there is no option to increase it. Any ideas?

---

### Post by mfdc1969 on 2007-12-18
I have the same card in an old computer running Fiesty Server that I use as a samba server in the crawlspace. I had similar problems until after all the synaptics/add & remove stuff I finally ran this command:

```
sudo dpkg-reconfigure xserver-xorg
```

But, I must admit I do this remotely as I have no monitor or keyboard on the box, it sits under the house and I use either vncviewer (if I want a graphical interface) or I just ssh into it through a terminal. It appears to work in vncviewer when I see it from my other computer *which leads me to believe it does* work to reconfigure the xorg settings - including the resolution. 

During the reconfigure process I had zillions of options for screen resolution and I chose only the 3 lowest ones which I knew would work for me. Much different then before where I was only presented with 2 very low res settings!

So now the disclaimer - I'm a total newb and I hope this helps but please don't rely solely on my words.

Cheers,
Mike

---

