---
title: "Need Help! My wireless connection seems capped."
date: 2012-10-06
forum: Networking &amp; Wireless
---

### Post by marvinmakie on 2012-10-06
Need Help! I recently installed ubuntu 12.04.1 on a thumb drive. All in all the OS run good but when i unplugged my local network connection and tried to connect my laptop to a wireless router it has a very poor bandwidth, cannot download files because it only speeds up to 30kbps but when i try to put back my connection to local network connection my download speed speeds up to 250kbps. 

I also tried downloading to an Windows with another laptop, it seems fine.

Im a newbie about ubuntu. Please Help me.


Sorry for my bad english.

---

### Post by bart.a on 2012-10-17
Have you tried updating your system while it's wired to the internet?

What wifi card/device are you using?
Are you using the ubuntu driver or the windows driver via [ndiswrapper]("http://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")?

---

### Post by patilsb on 2012-10-18
hi friends;
i have made a big misteck, my gnome network manager deleted by me, and now no internet connection on my ubuntu 12.04 [64 bit],very sad this time..... plz help me how to fix it again.[i have only samsung galaxy ace and nokia c1 01 for net use in windows xp; no wi fi, no ethernet, no cable net]

---

### Post by funicorn on 2012-10-18
The most convenient way that you can follow  to install network-manager back is to install it in the livecd, if you have one.

Insert livecd and boot it, and connect to internet. (If you can not, there is a problem with your network)

open gnome-terminal, type in following commands
```

sudo fdisk -l

```This one lists your partitions, find out the partition number of your root partition, which should be flagged with 'linux 83 '. In the following part I suppose it's 'sda5'
```

sudo mount /dev/sda5 /mnt

```This one mounts your root partition to /mnt
```

sudo chroot /mnt

```This one chroot current / from the livecd root to your physical system
```

sudo apt-get install network-manager

```
You may also need to install several other relative packages. Then exit gnome-terminal and reboot. Your network-manager is back.

Or else, you have to use command line to establish a wireless connection. I never type that myself, you need more googling.

> **patilsb said:**
> hi friends;
i have made a big misteck, my gnome network manager deleted by me, and now no internet connection on my ubuntu 12.04 [64 bit],very sad this time..... plz help me how to fix it again.[i have only samsung galaxy ace and nokia c1 01 for net use in windows xp; no wi fi, no ethernet, no cable net]

---

