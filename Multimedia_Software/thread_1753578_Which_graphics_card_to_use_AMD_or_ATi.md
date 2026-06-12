---
title: "Which graphics card to use AMD or ATi?"
date: 2011-05-09
forum: Multimedia Software
---

### Post by sk4tec on 2011-05-09
Hi, trying to get Ubuntu to work properly on a Del Dimension 2400.
It has on board Intel Extreme graphics card.

[http://support.dell.com/support/edocs/systems/dim2400/en/sm_en/specs.htm]("http://support.dell.com/support/edocs/systems/dim2400/en/sm_en/specs.htm")

It installs and but runs slowly when the ubuntu GUI is up and running. The CPU is maxed out for quite small tasks. Selecting additional drivers gives nothing, so I guess it isn't running the graphics card in hardware acceleration - which is slowing down the system.

I want to buy a graphics card to use on this Dell PC. It uses PCI expansion cards. I'm thinking of ebaying a second hand graphics card.

So my question is which is more compatible ATI or Nvidia?

---

### Post by coffeecat on 2011-05-09
According to your link your machine has an Intel 845GV chipset which means that whatever fancy name they give the graphics (Intel 3D Extreme Graphics) it'll be the now very old 845G graphics. It might have been extreme in its day, but not now. In fact I had a machine with 845G graphics a few years ago and "extreme" would have been an - um - optimistic adjective to use even in its day. :wink:

Additional drivers won't give you anything because Intel graphics use the in-the-box open source Intel drivers which Intel help to develop anyway.

To your question, "which is more compatible ATI or Nvidia?", many people will give you the knee-jerk reaction of nvidia. I'll try to be slightly more nuanced. Generally speaking you are more likely to get good 3d acceleration if you choose a nvidia card and install the proprietary driver, but with a big caveat. Don't choose a very old chipset.

As far as ATI concerned, you will get perfectly good 3d acceleration and with the default open source driver with many, but not all, ATI cards. (Which is better than the current situation with nvidia if you want to use the open source nouveau driver. You cannot get 3d with nouveau unless you install an experimental package.) For example I'm far happier with my ATI Radeon HD4350 than I was with my previous nvidia card. And I'm just as happy with the Mobility Radeon HD4200 on my laptop.

Having said all that, your main limitation is your PCI interface. That is going to severely limit your choice. You don’t say where you are geographically so there's no point in my providing links to suitable cards from a UK supplier. Have a look on your favourite supplier's website and post links of some cards you think may be suitable and within your budget. Then people can comment on them.

---

### Post by sk4tec on 2011-05-09
Thank you for your reply. I'm not too concerned about 3d performance. It would just be nice to use Ubuntu on a supported graphics card. At the moment it seems that the CPU is doing all the work and even web pages over burden it!

I've found a gfx card which is a GeForce FX5200. Can anyone comment on if it may be compatible?

I presume changing my card is as simple as swapping the hardware, booting and selecting Additional Drivers under Administration and letting Ubuntu find the driver itself.

This guy is using it ok:

[http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.04-desktop-nvidia-geforce-fx-5200]("http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.04-desktop-nvidia-geforce-fx-5200")

---

### Post by coffeecat on 2011-05-09
Sorry - I misunderstood you. Your mention of hardware acceleration made me assume that you were trying to get 3d.

That link is for the now unsupported 9.04/Jaunty release of Ubuntu. The problem with older cards as time goes by is that newer versions of the xserver can break older drivers. I did a quick search for you in the now closed Natty testing subforum. Some members reported that they were able to run Natty with the fx5200 card but were unable to get Unity - the system defaulted back to classic gnome. But that would be so with any nvidia card with the default nouveau driver, and it wasn't clear from any of the posts whether these 5200 owners had tried installing the proprietary driver. Synaptic in Natty lists the older nvidia-173 driver which *should* support that card. It looks as though you may be OK with the latest version of Ubuntu.

See what others say too.

Good luck!

---

### Post by sk4tec on 2011-05-11
Right, got the card through. The system had 11.04 and I plugged it in and did the additional drivers option. It went away and found 1.73 (and another experimental driver). I chose 173, after a while it's status was 'installed but not in use'. Compiz didn't work which led me to thinking that 2d and 3d acceleration weren't working.

Did a clean install of 10.10, this time driver is found and 'appears' to be in use. But again no compiz screen i-candy. I have got the Nvidia settings page under Preferences.

All in all it ran *faster* in 11.04 - tested using bbciplayer, even though the driver wasn't in use. 10.10 install - driver appears to be in use but runs slower!

Are there any graphics tests (ie spinning cubes etc) to see if the hardware acceleration is running?

I don't really know linux under the hood, so everything does need to be spelled out (... so I can cut and paste it!)

Many thanks.

---

