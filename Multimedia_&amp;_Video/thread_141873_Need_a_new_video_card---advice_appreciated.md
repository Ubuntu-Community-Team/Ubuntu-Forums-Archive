---
title: "Need a new video card---advice appreciated"
date: 2006-03-09
forum: Multimedia &amp; Video
---

### Post by microserf on 2006-03-09
Hi

It looks like my video card has broken and I'll need a new one. I'm not a gamer, so I'm looking for something cheap and well-supported by Ubuntu. I currently have a Nvidia card.

Can you advise me what I should buy?

How do I perform the upgrade? Is it just a matter of replacing the card, or are there settings and drivers to mess with?

Thanks very much in advance.

---

### Post by frodon on 2006-03-09
I use use a nvidia fx5200, it's cheap and have good performances and it's perfectly supported by ubuntu.
If you change for another nvidia card, i think you should open your xorg.conf and use the nv drivers before changing your card then swich off your computer, install the card, start your computer and re-install nvidia drivers, you shouldn't have many problems, if you have just run a : ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bluevoodoo1 on 2006-03-09
I just bought an Evga geforce fx5500 for about $50 to replace my crummy ATI 9100 igp. I'm on it now, and surprisingly it only took a few minutes to set up.

Do you have PCI slots, PCIe, agp? 

My computer is rather dated and only has PCI, but that's fine since--like you--I'm not a gamer, but it can do nifty things now like the 3ddesktop switcher.

 I used a few guides [here]("http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia")... and [here]("http://www.ubuntuguide.org/#installnvidiadriver")... and "sudo dpkg-reconfigure xserver-xorg" a couple of times. (make sure you backup your xorg.conf file, just in case... (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup)

I followed the directions of the first thread and it all went very well. The only thing that almost stumped me was the  BusID "PCI:1:0:0" in the xorg.conf. Have to make sure it points to the location of the new card. For me it kept pointing to the onboard video. But like I said it was pretty quick, in less than 30 minutes it was working.

There are a bunch of guides to work from and many people around here like nvidia over ati. I made the jump and I am happy I did.

---

### Post by microserf on 2006-03-09
Thanks all---much appreciated.

---

