---
title: "Ati HD 3450 + Dual Head Problems"
date: 2009-03-30
forum: Multimedia Software
---

### Post by gelito on 2009-03-30
Hi,

I have two weeks trying to put two monitors on Ubuntu, I tried with the fglrx drivers, ati, radeon, with bigdesktop, xinerama, setting a hand ... And I could not get anything

My problem is that the graphics card only has a DVI-I output, so I had to buy a splitter (DVI-I x 2VGA). I've seen people out there who use splitters without problems, but when i put the two monitors, Ubuntu appears to be a mess with the settings...


My system:

PC: HP Pavilion Slimline s3422.es ([http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01410510&cc=us&lc=en&dlc=en&product=3709764](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01410510&cc=us&lc=en&dlc=en&product=3709764))

Graphic Card:  ATI Technologies Inc Mobility Radeon HD 3450 256MB

Monitors: Acer V223HQ & Hundai L70S+


No longer prove that. I thought of trying to use the graphics card on the motherboard (Foxconn) with ATI, but I can not activate it.

Any ideas for further testing? Someone could confirm me if the splitters recognize two monitors? Can you use the graphics on the motherboard?

And only someone knows any good Nvidia pci-e low profile?

Thank soo much for the help!

---

### Post by Linoobius on 2009-03-30
gelito,

If I'm understanding you correctly, I believe your problem lies in the type of splitter you are using. The DVI standard allows for two digital video signals and one analog signal. If you have a splitter that plugs into the DVI-I connector and has two VGA output connectors then the output on each of the two connectors would be the same unless the splitter is somehow converting the digital signal to analog (I have no specific experience with the splitters) I think you would need a splitter that had two DVI-D outputs or one DVI-D output and one VGA (analog) output. If you use DVI cables, be aware that there are multiple kinds of cables, DVI-I (Integrated single and dual link) DVI-A (Analog only), DVI-D (digital only single and dual link) the dual link cables carry both digital signals while the single link cables only carry one digital signal. There is a very informative wiki at:

[http://en.wikipedia.org/wiki/Digital_Visual_Interface]("http://en.wikipedia.org/wiki/Digital_Visual_Interface")

I hope this information leads you in the right direction,

Linoobius

---

### Post by gelito on 2009-03-31
Thx Linoobius, 

Now I understand a little better where you can be my mistake ... ;-)

Then, the only solutions: Enable the graphics card on the motherboard and use the two, or switch to another graphics card Nvida (better ATI) with two output...


Thx!

---

### Post by Linoobius on 2009-03-31
gelito,

I have an ATI 3450 card but I do not have it in a LP case. the VGA output is on a header cable above the DVI connector, the low profile bracket probably doesn't have room for the extra connector, you may check on the board itself to see if there is a header where you can pick up the analog video signal and route it to an open slot next to the 3450 card, not sure where you could pick up a VGA header/cable, maybe ebay or ATI.

Linoobius

---

### Post by Willleung on 2009-04-12
> **gelito said:**
> Hi,

I have two weeks trying to put two monitors on Ubuntu, I tried with the fglrx drivers, ati, radeon, with bigdesktop, xinerama, setting a hand ... And I could not get anything

My problem is that the graphics card only has a DVI-I output, so I had to buy a splitter (DVI-I x 2VGA). I've seen people out there who use splitters without problems, but when i put the two monitors, Ubuntu appears to be a mess with the settings...


My system:

PC: HP Pavilion Slimline s3422.es ([http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01410510&cc=us&lc=en&dlc=en&product=3709764](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01410510&cc=us&lc=en&dlc=en&product=3709764))

Graphic Card:  ATI Technologies Inc Mobility Radeon HD 3450 256MB

Monitors: Acer V223HQ & Hundai L70S+


No longer prove that. I thought of trying to use the graphics card on the motherboard (Foxconn) with ATI, but I can not activate it.

Any ideas for further testing? Someone could confirm me if the splitters recognize two monitors? Can you use the graphics on the motherboard?

And only someone knows any good Nvidia pci-e low profile?

Thank soo much for the help!

Ever try uninstalling the drivers, and reinstall the drivers with everything hook up?  it work for me, on a mobo 780G board graphic.  Tried to add a 3450 for a 3rd monitor, and it simply didn't work..

---

