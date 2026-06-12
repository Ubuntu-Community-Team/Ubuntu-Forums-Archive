---
title: "Changing Graphics Cards"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by theARE on 2006-08-01
I recently purchased a custom built computer and specified an Nvidia Graphics card. However when the PC arrived yesterday I eventually discovered that they had fitted an ATI card rather than the one I specified.

I have contacted them and they are sending me the correct card. 

Will I have to reinstall dapper to get the card to work correctly, or can I just boot the live cd with the new card installed and copy xorg.conf over to the hard disk?

I spent a lot of time setting thing up before I discovered the graphics card issue, and would rather not have to install from scratch if I can avoid it.

What approach would you guys recomend I take?

Thanks

---

### Post by MonkeyNet on 2006-08-01
You will not require a reinstallation of dapper at all. However, once putting the new card in, if you cannot get gnome running, you will have to use the terminal to reconfigure X.

I would suggest having a look at [Ubuntu Guide]("http://www.ubuntuguide.org/") for installing the nVidia drivers.

If you want to make sure that you are running the latest drivers, then you will need to follow the HOWTO [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Breezy")

Just be sure that if you use the latter to install the latest drivers, they will need to be recompiled with any change of the kernel.

Cheers,

Andrew

---

### Post by theARE on 2006-08-01
Ok, thanks I'll give it a try.

I've already installed the nvidia drivers, it was at that stage that I discovered that they had made a mistake with the card.

Hopefully all that I'll have to do is update xorg.conf and enable the drivers.

According the the PC company the replacement card should be here tomorrow.

I'll let you know the results!

---

