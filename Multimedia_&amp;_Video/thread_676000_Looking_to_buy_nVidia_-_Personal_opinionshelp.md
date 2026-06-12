---
title: "Looking to buy nVidia - Personal opinions/help"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by Condoulo on 2008-01-23
Ok, I am wanting to buy a new video card, probably nVidia, but one of my main concerns, is the new xorg auto-config tool in Ubuntu 7.10, which would not even allow me to access the live CD because it could not configure my ATI drivers correctly, so I want something that will allow me to get into the LiveCD and actually properly install Ubuntu and deal with the drivers later. I am also wanting to get a good card that is within a good price range, because I want to have 3D effects, and watch videos of course :popcorn:. I do some light gaming on my Windows install (Half Life 2 Death match is all I have right now)

I also want something that comes with a DVI to VGA converter, if possible. Please give me your suggestions.

---

### Post by mozetti on 2008-01-23
nVidia seems to work better than ATi. I have a GeForce 6200LE that has no problems running Compiz, playing video, or rendering some standard games. Can't remember if it came with a DVI->VGA converter.

---

### Post by odiseo77 on 2008-01-23
I haven't tried anything but nVidia, but I've read many threads here on the forum about people complaining because their ATI graphic cards don't work fine. According with my personal experience, nVidia graphic cards work very good on linux, and if you're using Gutsy, the driver installation will be as easy as opening the restricted devices manager and enabling the driver there.

---

### Post by disturbed1 on 2008-01-23
Mx4000 (PCI 64mb) fx5500 (AGP 128mb) 7600GT (PCIe 256mb) have all ran the live cd just fine.

Not sure about Halflife 2 Death Match. I haven't played a windows game besides COD2 for years. COD2 ran just fine with the fx5500. Even the lowly Mx4000 handled basic compiz effects without slow down.

Look for a card that does not have Turbo Cache. Stick to the 7300/7600/8500/8600/8800 line. GT is better than GS.

Some ATI cards need to be setup with VESA instead of the built in ATI/Radeon driver. This driver does not support cards including and beyond the x1xxx line. Ubuntu detects an ATI card, and attempts to use the ATI driver. An easy work around is to just use "safe graphics mode".

---

### Post by RebounD11 on 2008-01-23
> **disturbed1 said:**
> Mx4000 (PCI 64mb) fx5500 (AGP 128mb) 7600GT (PCIe 256mb) have all ran the live cd just fine.


+1 for 7600GT. I have one of those and it's awesome. If you need one on PCI-e it's cheaper than that on AGP. 

If you want one that you would use in Windows Vista and play DirectX games I would recommend 8600GT or GTS, although in Linux the difference between 7600 and 8600 in virtually 0.

I would also recommend sth from ATI: HD2600Pro - a little harder to configure... but if you install the latest drivers from ati.amd.com and set them up correctly (on Ubuntu they didn't work for me from the beginning - worked eventually - but every other distro was OK), you will have great video performances :)

---

### Post by jbysmith on 2008-01-23
My system is still AGP based.  I used to use an ATI X850, which is a pretty decent card (in Windows).  Under Linux it was horrible.. I have no experience with the current state of ATI drivers however.

I switched to a Radeon 7800 GS OC, and I haven't looked back.  Works flawlessly under Ubuntu using the Envy script for the nVidia drivers.  The only manual editing I needed to do was for getting full 8X AGP, fastwrites etc enabled.  The resolution and such itself is all done nicely with the GUI apps.  Great performance.  Get a FPS hit when playing games with Compiz running of course, but it's actually not bad.  I can play World of Warcraft with Compiz running with an acceptable performance.  Turn off Compiz and its Windows like.  I keep a small Winders partition handy for a few games, and runs very very well in that too.   The 7800's are reasonably inexpensive nowadays too.

---

### Post by cooltd825 on 2008-01-23
i'm not sure if you've seen them, but there are numerous threads floating around here about having driver issues on the 8xxx series.  i actually can't even load Linux anymore because of this, and i have the 8500GT.  but i would definitely recommend this card if you're short on the cash.  it's not that hot out of the box, but it overclocks like you wouldn't believe.  with a custom cooler i can crank this thing up to 700 core 1040/520 mem and it runs just fine.  it'll even take Crysis on medium with 40+ fps.  i can imagine the 8600 would be able to take this kind of punishment too.

---

### Post by Nibes on 2008-01-23
Geforce Pcx5300, having issues with drivers. But It really works great with 3D effects of compiz. The related issues are: ubuntu wont finish his shutdown so you will have to press the power button.

---

### Post by Shazaam on 2008-01-23
AGP= GeForce 7800, 7900 or 7950. Any type (plain vanilla, GS, GT, GTS) Stay away from SE and LE AGP video cards for Windows games.
I run a 7800gs OC and I haven't had any problem with any Linux drivers (except when I first started with linux which was a human error) and Gutsy's desktop effects work fine.

---

### Post by wolfen69 on 2008-01-23
> **disturbed1 said:**
> 

Look for a card that does not have Turbo Cache. Stick to the ***7300***/7600/8500/8600/8800 line. GT is better than GS.



stay away from the 7300 cards. they have known issues with new nvidia drivers.

---

### Post by disturbed1 on 2008-01-23
> **wolfen69 said:**
> stay away from the 7300 cards. they have known issues with new nvidia drivers.

I forgot about that. Something to do with multicore CPUs? Would thought it would have been fixed by now.

---

