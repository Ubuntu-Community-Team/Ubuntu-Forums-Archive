---
title: "Interwebs"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by LiveToPoop on 2010-02-06
Hi, I am a new linux user. I have been on snow leopard and widnows 7 all my life. I just installed ubuntu on my other computer and I can't connect to the internet. Someone said that [IMG]http://i45.tinypic.com/35l7sxl.jpg[/IMG] this little logo should be on the screen, but it is not. That picture of the two screens is absent on my screen. I need to connect to the internet. Please tell me how to connect to my wireless network with or without the little image on the screen. PLEASE HELP!

---

### Post by mörgæs on 2010-02-06
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by LiveToPoop on 2010-02-06
> **mörgæs said:**
> [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
 
Not helpfull at all.](*,)I AM SOOOOO FRUSTRATED

---

### Post by mörgæs on 2010-02-06
> **LiveToPoop said:**
> Not helpfull at all.](*,)I AM SOOOOO FRUSTRATED

This is your conclusion after only 10 minutes?

---

### Post by Iowan on 2010-02-06
There may be another way to do it, but...
Open a terminal (Applications>Accessories>Terminal), enter **sudo lshw -C network** - post results.

---

### Post by mushwars on 2010-02-06
alt + f2 then type
```
**nm-applet**
```

this WILL start the applet if it doenst do this..

```
sudo apt-get install network-manager
```

then start the nm-applet.

If this doesnt work I am REALLY supprised.

you could then try 
sudo apt-get purge network-manager
then sudo apt-get install network-manager

you might need to boot the live cd then chroot into your partiton... do that this way:

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo chroot /mnt/ubuntu
```

then make sure you are connected to the internet with the wifi manager on the live cd then apt-get install network-manager

**read that ^ and it will work again**

---

