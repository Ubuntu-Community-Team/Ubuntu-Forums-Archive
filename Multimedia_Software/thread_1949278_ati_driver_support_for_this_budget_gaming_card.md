---
title: "ati driver support for this budget gaming card"
date: 2012-03-29
forum: Multimedia Software
---

### Post by supernater on 2012-03-29
I was looking to get a budget gaming card and I saw this article on tomshardware....

[http://www.tomshardware.com/reviews/best-graphics-card-game-performance-radeon-hd-6670,2935-2.html](http://www.tomshardware.com/reviews/best-graphics-card-game-performance-radeon-hd-6670,2935-2.html)

I have a 1680x1050 setup so the Radeon HD 5570 DDR3 looks like it might be what I want (it has to be better than my 9400GT card).  However, I was under the impression that ATI driver support is lagging behind NVIDIA.  Is this still true?  Would I have problems with this card?  Using Ubuntu 10.04.  Thanks.

EDIT:
Was also looking at the HD 6770.  Is the driver support okay for this card?  Here are the specs...
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814125386](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125386)

---

### Post by Yellow Pasque on 2012-03-29
If you're looking to game on Linux, save up for an nvidia card (gtx 550ti).

In case you're wondering, I personally prefer Radeon cards using the open-source radeon driver, but I'm not a gamer.

---

### Post by supernater on 2012-03-29
I don't game much on linux.  I dual boot Windows.  I found this link...

[http://askubuntu.com/questions/49543/how-to-install-ati-radeon-6770-drivers-on-10-04](http://askubuntu.com/questions/49543/how-to-install-ati-radeon-6770-drivers-on-10-04)

It seems it is supported.  So all I do is download and run the installer?  What about when I update my kernel or xorg?  Do I have to reinstall the drivers?  I hope that is not the case.  With my current Nvidia card I just used the "restricted drivers" program that came with Ubuntu.  I installed once and never had to worry about it again.  Is this the case with ATI?  Thanks.

---

### Post by Yellow Pasque on 2012-03-29
Better install instructions are here: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)
If you use that method, then the driver is automatically updated (using dkms) when installing a new kernel.

---

### Post by supernater on 2012-03-30
> **Temüjin said:**
> If you're looking to game on Linux, save up for an nvidia card (gtx 550ti).

I was wondering if you could elaborate on this?  I have used Nvidia for a while now but I was really curious why Linux gamers avoid ATI/AMD cards.  Are they inferior?  I saw a few youtube videos of linux gamers playing 3d games using ATI cards.  Here is one...

[http://www.youtube.com/watch?v=p9vfHTPl6y8](http://www.youtube.com/watch?v=p9vfHTPl6y8)

Are ATI cards simply inferior to Nvidia with respect to gaming?

---

### Post by mastablasta on 2012-03-30
> **supernater said:**
>  
Are ATI cards simply inferior to Nvidia with respect to gaming?
 
not cards themselves, but drivers were problematic. however this is turning arround fast lately.

---

### Post by supernater on 2012-03-30
> **mastablasta said:**
> not cards themselves, but drivers were problematic. however this is turning around fast lately.

What exactly were the problems with these drivers?  Was 3D acceleration an issue?

---

### Post by marinara on 2012-03-31
I'm runninng 2 computers with ATI cards.  I didnt have problems at first, but even small problems become more annoying when you can't fix em

---

### Post by supernater on 2012-03-31
> **marinara said:**
> I'm runninng 2 computers with ATI cards.  I didnt have problems at first, but even small problems become more annoying when you can't fix em

Well, I managed to get a HD 6770 for about $80.00.  I couldn't refuse at that price.  What kind of problems can I expect?  

The link Temüjin posted seemed to indicate that it was as easy at enabling "ATI accelerated graphics driver" in the restricted drivers program and that this would install the catalyst 8.723 drivers.

There is also a section that says I need to run
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install fglrx
```

I looks like I can pick one or the other.  I'm just not sure which.  As soon as I get the card I'll post back here if I have any problems.  Hopefully I won't regret getting an ATI card!

---

### Post by marinara on 2012-04-01
i'm using lubuntu, with ATI i get tearing when playing videos with VLC
um
some problems with alt-printscrn+k

clunky drivers wanted to put a black border around the screen for some stupid reason.  

everything works, it's just the catalyst control center doesn't really work 100%.  more like 80%-90% so it's pretty buggy.  Like changing screen resolutions, etc.

---

### Post by supernater on 2012-04-06
> **Temüjin said:**
> Better install instructions are here: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)
If you use that method, then the driver is automatically updated (using dkms) when installing a new kernel.

I was looking at the instructions here and it looks like they create a new fglrx package.  However, these packages are available in the Lucid repository.  Shouldn't I just install those?  What is the difference?  Thanks.

---

### Post by Yellow Pasque on 2012-04-06
The drivers available in the Lucid repo are relatively old (older than your hardware)..
So build manually.

---

### Post by supernater on 2012-04-07
Oh okay.  I followed the instructions and everything appears to be working fine.  0 A.D. is running great!  However, WINE emulation of Guild wars is particularly bad.  I'm not sure how to fix it.  It ran better under my NVIDIA 9400 GT.  Some aspects of the game, such as the characters faces, don't even show up making my characters look like faceless blobs.  Maybe I should try reinstalling WINE.  Any pointers would be helpful.  Thanks.

---

### Post by Yellow Pasque on 2012-04-07
You can get latest wine with:

```
sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```

---

### Post by supernater on 2012-04-07
Thanks. Just added it.  That seems to have done the trick.  I had to turn off pixel shaders before it would work, but it appears to run well.   There is some shading issues with it, but I also had those issues with my old NVIDIA card.  I see a slight increase in frame rate.  My old NVIDIA 9400 GT would get 8-20 fps with Guild Wars using WINE, my new Radeon HD 6770 gets 30-50 fps using WINE.  Of course this is not near as good as with Windows (60 fps there) but it is much better than before.  Overall I'm glad I tried this card.  Since it's ATI/AMD I was expecting to have serious issues with it but so far it's been almost trouble free.  Just had to tweak a few things.

---

### Post by supernater on 2012-04-07
One more thing.  Is there a way to tell what my GPU temperature is?  Or a command that will tell my my GPU stats (temp, load, etc.)?  Thanks.

---

