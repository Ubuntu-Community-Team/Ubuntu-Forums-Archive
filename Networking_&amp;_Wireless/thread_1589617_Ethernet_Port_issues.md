---
title: "Ethernet Port issues"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by -gabe-noob- on 2010-10-06
Hey guys, major problem. I installed Ubuntu about a week ago; but I think this error is totally unrelated, just posting here to double check. 

Today while my brother was browsing the web on my windows partition he had a blue screen pop up, one of the soft/hardware error ones, not a true BSOD, anyways, ever since my lan port on the computer seems to not be activiating as no wired connection is recognized. The lan port/card is directly attached to the Mother Board, it's a gigabyte motherboard in a self-build computer. I'm just wondering if there's anything I can do to troubleshoot this and see if it is truly a hardware problem or if its something else. 

Thanks 

-nooby-gabey-


THIS IS A REPOST FROM GENERAL HELP. IF I SHOULD DELETE THAT THREAD PLEASE LET ME KNOW 
-Gabe

---

### Post by e79 on 2010-10-06
I'm not sure if I correctly understand the problem. Is your network card is no longer detected in Windoze as well as Ubuntu or is it strictly a Windoze problem ? If both OS can't see the Network Card anymore since this BSOD (or so), I would think its a hardware related problem. Can you boot from a LiveCD and see if the problem occurs as well ? If so, you could be practically 'sure' that your hardware is going haywire (which I hope not for you).

---

### Post by -gabe-noob- on 2010-10-06
Well, they both detect that there is a card in place, but its actual port isn't turning on I think. Its in all OS's, even the live CD that the port isn't working. Weirdly, the USB ports on the same mount as the ethernet port are working when the ethernet port is turned on in the bios, but not working when the ethernet port is turned off in bios. 

I don't think I'm describing it quite right, but I think I'm gonna need to buy one of these:

[http://www.newegg.com/Product/ImageGallery.aspx?CurImage=33-106-121-TS&ISList=33-106-121-S01,33-106-121-S02,33-106-121-S03,33-106-121-S04,33-106-121-S05&S7ImageFlag=1&Item=N82E16833106121&Depa=0&WaterMark=1&Description=Intel%20PWLA8391GT%2010/%20100/%201000Mbps%20PCI%20PRO/1000%20GT%20Desktop%20Adapter](http://www.newegg.com/Product/ImageGallery.aspx?CurImage=33-106-121-TS&ISList=33-106-121-S01,33-106-121-S02,33-106-121-S03,33-106-121-S04,33-106-121-S05&S7ImageFlag=1&Item=N82E16833106121&Depa=0&WaterMark=1&Description=Intel%20PWLA8391GT%2010/%20100/%201000Mbps%20PCI%20PRO/1000%20GT%20Desktop%20Adapter)

---

### Post by e79 on 2010-10-06
> **-gabe-noob- said:**
> Well, they both detect that there is a card in place, but its actual port isn't turning on I think. Its in all OS's, even the live CD that the port isn't working. Weirdly, the USB ports on the same mount as the ethernet port are working when the ethernet port is turned on in the bios, but not working when the ethernet port is turned off in bios. 


Yup, it really seems that it is a hardware related problem. If everything was working fine before this BSOD but since, even a live CD cannot activate the ethernet card, you better go buy a new one as something went wrong in your mobo.

just my 0.02$

---

### Post by -gabe-noob- on 2010-10-06
I have an Gigabyte AMD mobo; would that chipset that I linked fit? I can't really tell.

---

### Post by e79 on 2010-10-06
> **-gabe-noob- said:**
> I have an Gigabyte AMD mobo; would that chipset that I linked fit? I can't really tell.

Well it only needs a standard PCI slot, so if you have one available, it will fit in. As for Ubuntu compatibility, after browsing the comments on newegg.com, it seems it should work without problems (see Intel_PWLA8391GT.png).

---

### Post by robsoles on 2010-10-06
> **-gabe-noob- said:**
> I have an Gigabyte AMD mobo; would that chipset that I linked fit? I can't really tell.

It's more a matter of the physical connection(s) rather than the chipset for an addon card like that. Check the free slots in your motherboard, a standard PCI slot should accommodate that card and it should operate fine with any mobo that has PCI slot(s).

[http://en.wikipedia.org/wiki/Conventional_PCI#Conventional_hardware_specifications](http://en.wikipedia.org/wiki/Conventional_PCI#Conventional_hardware_specifications) may be worth looking at for you.

---

### Post by -gabe-noob- on 2010-10-06
Cool, yeah I've got two free pci's and 1 free PCIe. 

And just for the sake of me continuing to be dumb; is there any chance that the ethernet port is just not drawing any power and that a plug got knocked loose some where? I checked it over and everything looks in order, but perhaps there's something I missed? Though I think if hte mobo's got power it should have power unless its fried.

Oh well

 thanks guys; and thanks for putting up with my stupidity

---

### Post by e79 on 2010-10-06
> **-gabe-noob- said:**
> 
And just for the sake of me continuing to be dumb; is there any chance that the ethernet port is just not drawing any power and that a plug got knocked loose some where? I checked it over and everything looks in order, but perhaps there's something I missed? Though I think if hte mobo's got power it should have power unless its fried.

I wouldn't think a cable got loose by itself, unless you shake & baked your rig  :lolflag:
And your logic seems ok, if the mobo gets power but the NIC doesn't, it is probably defective.

Glad we could help

---

### Post by robsoles on 2010-10-06
Although, with BSOD like that, it is more likely that the ethernet nic on your mobo has died - have you tried an alternative ethernet cable on the connection? (forgive me if already asked, I only skimmed previous posts!)

---

### Post by -gabe-noob- on 2010-10-06
Yup, a new Ethernet cable does nothing to alleviate the issue. Oh well, 3 days with no interwebs on my main box. No big deal.

---

### Post by -gabe-noob- on 2010-10-09
The new port installed easily and works fine out of the box. Thanks guys! :D

---

