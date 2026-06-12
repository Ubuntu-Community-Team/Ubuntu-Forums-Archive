---
title: "switching from on board chip to PCIe card on HP dc 7100"
date: 2011-04-08
forum: Multimedia Software
---

### Post by oldsoundguy on 2011-04-08
Yep,that is what I am trying to do.

Have an HP dc7100 Convertable Tower.  Have already installed Ubuntu 11.04  on it and then installed Mythbuntu via the repositories in an attempt to make it into a PVR. (installing the stand alone Mythbuntu did not give me much in the way of computer utilities/options, so I chose the alternate method.)
The install works fine on the existing on board video and I have progressed to setting up the Myth internals and realized that the on board video would not cut it in driving my HDTV theater set up and I would have to upgrade the video system.
Purchased a NVidia GT430 and tried to install it in the PCIe slot to no avail.
When I get the card in, no display .. and the on board display dies if there is a video card in the PCIe slot.  NO display off of either set up.  Remove the new card and the on board works again.
Bios is no help for disabling the on board and, thus far, have not found instructions for disabling it in UBUNTU .. lots of help if the box had Windows on it .. can find nothing otherwise.
I am sure this issue has come up before, but trying to search this site for a "fix" (for anything BTW) is getting more difficult as each day passes and the site grows.  Internal search engine needs some serious work/tweaking!
Google, thus far, has been SOME help, but everything comes back to having to use Windows to disable the on board.
Have found the CMOS reset switch on the motherboard, but never utilized that method before, so have no idea on the steps that have to be done prior to "pushing the button."
Current on board  chip is the 829156/GV/9106GL Intel.
F10 into bios does not lead to any ability to disable anything on board.
Had no issues with the on board sound disabling itself when I installed the Creative digital audio card.
It is just that damn video that has me at a road block.

Any ideas or REAL links that work?

Thanks

---

### Post by oldsoundguy on 2011-04-11
still no joy!  There just has to be a way other than putting Windows on the box to get this accomplished.

---

### Post by Yellow Pasque on 2011-04-11
Does an Ubuntu 11.04 LiveCD work with the nvidia card? Can you boot to recovery mode and use failsafe graphics?

---

### Post by walt.smith1960 on 2011-04-11
> **oldsoundguy said:**
> still no joy!  There just has to be a way other than putting Windows on the box to get this accomplished.

I'm not familiar with HP but is this of any help? It looks like the last few pages might be of some use.

[http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=430118&targetPage=http%3A%2F%2Fbizsupport1.austin.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc00244461%2Fc00244461.pdf]("http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=430118&targetPage=http%3A%2F%2Fbizsupport1.austin.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc00244461%2Fc00244461.pdf")

---

### Post by oldsoundguy on 2011-04-11
No the live CD won't even boot when I try and utilize the new PCIe card.  NO DISPLAY. the on board and the PCIe are fighting each other.

waltsmith .. broken link.

I have XP Pro on a drive I can toss in and utilize if need be, but wish there was a Linux solution instead.

---

### Post by walt.smith1960 on 2011-04-12
> **oldsoundguy said:**
> 

[B]waltsmith .. broken link.
[/B] 
I have XP Pro on a drive I can toss in and utilize if need be, but wish there was a Linux solution instead.

Sorry.  How about this?  
[http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?lang=en&cc=us&prodClassId=-1&contentType=SupportManual&prodTypeId=12454&prodSeriesId=410112](http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?lang=en&cc=us&prodClassId=-1&contentType=SupportManual&prodTypeId=12454&prodSeriesId=410112)
Scroll down about 2/3 of the way under _user guide_ "Computer Setup (F10) utility guide." The last couple pages mention selecting video adapters, specifically pages 27 & 28:

Inserting a PCI or PCI Express video card
automatically disables Integrated Video.
When PCI Express video is on, Integrated
Video must remain disabled.

---

### Post by Yellow Pasque on 2011-04-12
What version BIOS are you using?
```
sudo dmidecode -t bios
```

---

### Post by oldsoundguy on 2011-04-12
waltsmith.. wrong guide. there is no pg 27-28 on that one.  Thanks anyway, but I have the convertible tower .. not the tiny box that only takes lo profile cards.

And as I noted .. IF I put in the PCIe card there is no video signal from EITHER card.  (once again attempting to install a EVGA/NVidia GT430)

temujin.. it has Revision 2.15 on it currently.

---

### Post by walt.smith1960 on 2011-04-12
> **oldsoundguy said:**
> waltsmith.. wrong guide. there is no pg 27-28 on that one.  Thanks anyway, but I have the convertible tower .. not the tiny box that only takes lo profile cards.

And as I noted .. IF I put in the PCIe card there is no video signal from EITHER card.  (once again attempting to install a EVGA/NVidia GT430)

temujin.. it has Revision 2.15 on it currently.

I'm wondering if there's some setting in the BIOS (or whatever HP calls it) that is saying it can **only** use the integrated graphics.  Then when you plug in a PCIe card, the box wants to turn off the integrated graphics and use the PCIe card .  It can't turn off the integrated graphics because there's a BIOS setting that says it  **must** use the integrated graphics.  Electronic  standoff, both can't be active so neither one is active. Or something along those lines.  This doesn't seem like something the O.S. could control.  Perhaps with the BIOS replacement software starting to appear but with a conventional BIOS?

---

### Post by oldsoundguy on 2011-04-12
from what I have been reading, it seems that the card driver has to be installed using Windows as you have to remove the old driver and install the new one in order to get it to work.  Why they bypassed the BIOS is beyond me!
(apparently what happens is that when you change drivers, it re-flashes the CMOS with the new driver information.)

More and more it is looking like I will have to put that Windows drive in and do the deed that way.  Going to visit the tech shop I frequent now and then and do some mind melding first.

---

### Post by Yellow Pasque on 2011-04-12
> **oldsoundguy said:**
> from what I have been reading, it seems that the card driver has to be installed using Windows.
Citation, please (because I really doubt that). If you get no video signal during POST, the problem is independent of OS.

---

### Post by JGReen1996 on 2011-04-12
> **oldsoundguy said:**
> yep,that is what i am trying to do.


Have found the cmos reset switch on the motherboard, but never utilized that method before, so have no idea on the steps that have to be done prior to "pushing the button."

thanks
don't press the button unless you are experienced with flashing the bios/cmos it will leave your computer unable to boot

---

### Post by oldsoundguy on 2011-04-26
follow up.  Tried everything in my bag of tricks short of installing Windows to no avail.
So it is in the shop and letting the crew there have a shot at it and see if they can diagnose the issue and get the da*n video card installed.  HAVE to have HDMI as it IS Ubuntu with the Myth option installed and it is destined to be a PVR and feed my big screen.

To all that tried to help, thanks.

---

### Post by chkneater on 2011-04-27
something I've heard of before that might be a little safer than flashing the cmos is to take out the internal battery on the mother board after unplugging everything, press the power button a couple of times to discharge the caps and leave it alone for a half hour or so, but the batt back in and reconnect and reboot.  sometimes that will make the cmos "forget" but not have to be flashed. Good luck.

---

