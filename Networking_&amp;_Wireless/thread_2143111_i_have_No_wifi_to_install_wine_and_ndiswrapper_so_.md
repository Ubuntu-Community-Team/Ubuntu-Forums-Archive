---
title: "i have No wifi to install wine and ndiswrapper so i can go online"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by althalus2058 on 2013-05-07
i seem to be stuck in a bad loop of doom for me. i am new to Ubuntu and still learning so i am a tad bit slow but i don't have a wired router i can access for my computer to connect it to the internet so i have to use a net-gear wnda3100 for my internet needs. but here is my problem i don't have internet on that computer (I'm using my friends to send this) so i cant use the software center to install ndiswrapper and wine so how can i go about this.

---

### Post by Bucky Ball on 2013-05-07
Welcome to the forums.

You can type this in a terminal:

```
sudo lshw -C network
```

... and post the output back here. What makes you think you need Wine (can't see why) and ndiswrapper (largely superseded)???

Also, you don't mention what release you are using. Your best bet is to get to a wired router, get online, do an update and check 'Additional Drivers' if the card is not working by then. You may need a restart.

---

### Post by althalus2058 on 2013-05-07
i thought i needed it because reading online thats what it said i needed as well as ndiswrapper. i am running Ubuntu 13.04. and it said    PCI (sysfs)

---

### Post by althalus2058 on 2013-05-07
also i dont have the ability to use i wired router because of my internet situation

---

### Post by Bucky Ball on 2013-05-07
Then probably your only option is to download everything you need on a computer that is online, dump it to a USB dongle or some other media, then install on your machine. That or buy hardware that works out of the box with Ubuntu rather than having to jump through Wine and ndiswrapper hoops. You can pick up a compatible wireless dongle for next to nothing now days.

---

