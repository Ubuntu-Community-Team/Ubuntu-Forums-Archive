---
title: "No network devices available"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by brallan on 2012-05-05
Just installed ubuntu 10.04 onto my netbook with a Broadcom 4727 wireless LAN card and an Atheros AR8152 Ethernet controller. When i check the network  connections icon on the taskbar, i get the message "No network devices  available"

I have to update all the drivers and such since its a fresh  install of ubuntu but i can't get connected to the internet either  through wifi or lan. Help?

---

### Post by poolet on 2012-05-06
try the following and paste the output::

```
dmesg | grep -e wl -e eth1
iwconfig
sudo iwlist eth1 scan
```

---

### Post by brallan on 2012-05-06
thanks poolet. I mostly figured it out, though it wasn't easy:

I followed pythes's instruction in this post: [http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)

I thought I was configuring the LAN card and lo and behold the wireless card started working!

since there is no CDrom on the aspire one I also needed to mount the lucid image so that apt could get to it, which wasn't easy:

[http://ubuntuforums.org/archive/index.php/t-35807.html](http://ubuntuforums.org/archive/index.php/t-35807.html)

But even after overcoming these serious hurdles and running update manager, there were still many other issues (ethernet, video resolution, mike), so I decided to give up on 10.04. I will have a look at a few other options, perhaps xubuntu or mint. I've been extremely happy with ubuntu for four years (and for the last two with 10.04), but both unity and the poor functionality of gnome-failback in 12.04 are frustrating

---

### Post by poolet on 2012-05-06
> **brallan said:**
> thanks poolet. I mostly figured it out, though it wasn't easy:
 
I followed pythes's instruction in this post: [http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)
 
I thought I was configuring the LAN card and lo and behold the wireless card started working!
 
since there is no CDrom on the aspire one I also needed to mount the lucid image so that apt could get to it, which wasn't easy:
 
[http://ubuntuforums.org/archive/index.php/t-35807.html](http://ubuntuforums.org/archive/index.php/t-35807.html)
 
But even after overcoming these serious hurdles and running update manager, there were still many other issues (ethernet, video resolution, mike), so I decided to give up on 10.04. I will have a look at a few other options, perhaps xubuntu or mint. I've been extremely happy with ubuntu for four years (and for the last two with 10.04), but both unity and the poor functionality of gnome-failback in 12.04 are frustrating
 
It's not about the gnome or something.. :) some times it's better to search about flexibility (stable).....I am using 10.04 for the last 2 years and i think, i will never change it ;) it's not only the gnome, but the performance are better (plus are more friendly.. :) at least for me.!!! )... I dont blame other versions - kernal's or something (since I have ever used except debian which are terrifically!!!!!! but not with dual cpu!!) but as I make a reasearch I agree with you, the gnome it's very frustrating at any newest versions that I have try..!!!

---

