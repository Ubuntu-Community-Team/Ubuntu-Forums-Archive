---
title: "Recommended Dedicated Frontend H.264 hardware"
date: 2010-10-07
forum: Mythbuntu
---

### Post by pilesofspam on 2010-10-07
Spent some time searching the forum and couldn't come up with a clear answer (outside of an expensive one).  The mythtv frontend wiki page is pretty outdated.

I've got a mythbuntu system with OTA HD (from an HD5500), Dish HD from a Hauppage HD-PVR, and dish SD from a PVR-150.  Combination FE/BE has been working perfectly for a while, using VDPAU for playback.

I'd like to expand this system by installing a dedicated FE upstairs.  Getting an ethernet cable there is no problem.  Can anybody recommend the cheapest option for a FE that can handle the H.264?  I'm thinking Celeron or Sempron based system with a fanless Geforce 8400.

The TV upstairs is currently SD (vga input) but will be upgraded in the future to HD.  Ideal output is DVI and 2 channel audio.

The other option, I guess, is get a uPNP player, but you miss a lot of features that way.

Thanks for any recommendations!

---

### Post by LowSky on 2010-10-07
Acer Revo with Nvidia ION (ION is a 9400 seires GPU I think) works great.
They have both VGA and HDMI outputs too

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&IsNodeId=1&Description=acer%20revo&bop=And&Order=PRICE&PageSize=100](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&IsNodeId=1&Description=acer%20revo&bop=And&Order=PRICE&PageSize=100)

---

### Post by ian dobson on 2010-10-07
Hi,

Look at atleast a NVidia 9300 graphic card. The 8x00 series don't have full hardware support for VDPAU.

If you get vdpau up and running with a good NVidia card, you won't need any CPU power. My frontend is a C2D e5200 (Dual Core 2500MHz) that I've underclocked to 1200MHz and it can still play everything I can throw at it (h264 mkv 1080p) as the graphic card (Undeclocked 9600gt) does most of the work. The cpu load is between 10-20% max. when playing back a mkv with 5.1 sound.

Regards
Ian Dobson

---

### Post by pilesofspam on 2010-10-07
LowSky:  Thanks!  That looks like it definitely fits the bill.  Only painful part is the $262 pricetag for an open box version.

Ian:  Thanks for the recommendation- I do have a fanless 8400GS in the combination FE/BE and vdpau works great with a 10% CPU use (underclocked 3600X2).  The only problem I have is that I'm running 9.10 and the FE occasionally crashes (the BE keeps ticking along just fine) when exiting watching a program (live or recorded).

I'm looking to back up my movies and music and then start over with the latest release, but I'd like to have a remote FE ready to install as well.

---

### Post by LowSky on 2010-10-07
pilesofspam I had a similar problem with crashing.. let me guess that 8400 only has 256 or 512 RAM. For some reason the VDPAU driver likes to see 1GB of video RAM for 8x00 series cards. No idea why.

you can try upgrading the Nvidia 260 driver it might help
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

I went the expensive route and repaced it with a newer GTX460 (I know its overkill but I also game) and the problem went away.

---

