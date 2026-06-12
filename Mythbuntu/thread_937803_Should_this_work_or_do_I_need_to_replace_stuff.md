---
title: "Should this work or do I need to replace stuff?"
date: 2008-10-04
forum: Mythbuntu
---

### Post by WeeGraeme on 2008-10-04
I've previously posted a question related to part of this problem, but I'm still frustrated by it all.  I don't particularly just want someone to fix it for me, but after 5 weeks, I'm still no further advanced than I was at the start.

Here is my hardware:

Asus M3N78-VM AM2+ GF8200 5200MT DDR2 PCIEx16 RAID GbLAN mATX motherboard
AMD Athlon™64 X2 4850e AM2 45w Energy Efficient CPU
Dvico Fusion Dual 4 Dual Express Hybrid Digital PCI express
2 gigs Kingston DDR2
Asus EN9600GT 1GB DDR3 PCIE2.0 HDTV 2xDVI-I HDMI HDCP

What I want to be able to do is:

Set a suitable video resolution.  No matter what version of the Nvidia drivers I install, it always comes up in low resolution and won't configure to greater than 800 x 600.  I've got it connected to a 46 inch HD LCD TV, but the driver thinks it's a 7 inch screen.

I haven't been able to get a single sound from the SPDIF header into the video card.  I have managed to get it to work when I've installed Windows XP Home on the same machine.

I want to setup composite input to record Austar (pay tv) programming.  Needless to say, with the first two issues unresolved, I haven't even started to look at this.

I'm wondering if someone can tell me if these are achievable.  If I need to replace this hardware, so be it.  I can't believe that after trying to configure this for 5 weeks, I'm still no closer than when I first started.

I don't want to give up on this project, but I'm not that far from making this into a $1000 frisbee.

---

### Post by ttabbal on 2008-10-04
> **WeeGraeme said:**
> 
Set a suitable video resolution.  No matter what version of the Nvidia drivers I install, it always comes up in low resolution and won't configure to greater than 800 x 600.  I've got it connected to a 46 inch HD LCD TV, but the driver thinks it's a 7 inch screen.

Try disabling EDID. TVs like to send bad data about what they can/can't do. Just disable it and tell the video card what you have in xorg.conf. Are you using the nvidia binary driver or the nv OSS driver? You should post your xorg.conf and Xorg.0.log. Have you tried the HDTV options like Option         "TVStandard" "HD720p".

> **WeeGraeme said:**
> 
I haven't been able to get a single sound from the SPDIF header into the video card.  I have managed to get it to work when I've installed Windows XP Home on the same machine.

Have you configured SPDIF as the output in the TV playback settings? There is a whole wiki topic on setting up digital out on the MythTV wiki. Can you connect directly from the header to the amp to see if there is something about the video card that's throwing things off? That feature might not be supported in the Linux drivers. 

> **WeeGraeme said:**
> 
I don't want to give up on this project, but I'm not that far from making this into a $1000 frisbee.

Honestly, the hardware looks OK to me. I'm not that familiar with DVB, but from what I've read, it should work. If anything, the video card is overkill. I'm using onboard NV6150 to drive a 60" HDTV just fine. I'm using component though, DVI was causing problems for me that I never could get quite worked out. I was intentionally a little vague with settings and such. You sounded like you wanted to figure things out yourself.

---

### Post by newlinux on 2008-10-04
Have you tried using nvidia-settings? And yes, post your xorg.conf conf and log.

---

### Post by ltheriault on 2008-11-21
Have you gotten your sound working using SPDIF output on your 
Asus M3N78-VM?  I have managed to get everthing else working.  Let me know where your at...

---

### Post by agamotto on 2008-11-22
As stupid as this will sound, you might want to replace your video card with an older one.  You really don't need a card that powerful in a Mythbox.  I would suggest an older 6x or 7x nvidia card, as those drivers have been out for awhile.

---

### Post by ian dobson on 2008-11-23
Hi,

If you've got an older Nvidia card laying about try that.

I have a 7300lt in my frontend at the moment and due to an upgrade of a Gaming box I had a 8600 free. I tried the 8600 in my frontend but the results where worse than with the 7300 (High CPU usage when playing MPEG2 videos, SVIDEO output was abit blury). I later found out that xV (Hardware acceleration) isn't supported on newer cards.

Regards
Ian Dobson

---

### Post by JedTheHead on 2008-11-23
> **ltheriault said:**
> Have you gotten your sound working using SPDIF output on your 
Asus M3N78-VM?  I have managed to get everthing else working.  Let me know where your at...

Same here... I am trying to get SPDIF audio working.  Running XBMC and haven't go it to even light up as best as I can tell. 

Things I have done so far: 

- Got rid of pulseaudio because of the crackle, etc.  I had to move everything to Alsa.  Went into alsamixer and enabled the SPDIF / ice958.  Tried a few settings in the BIOS, hope to play with it more this afternoon and will report back what I find...

---

### Post by simongreen.net on 2009-01-14
> **JedTheHead said:**
> Same here... I am trying to get SPDIF audio working.  Running XBMC and haven't go it to even light up as best as I can tell. 

Things I have done so far: 

- Got rid of pulseaudio because of the crackle, etc.  I had to move everything to Alsa.  Went into alsamixer and enabled the SPDIF / ice958.  Tried a few settings in the BIOS, hope to play with it more this afternoon and will report back what I find...

Any update on this? I can't seem to get the SPDIF working either.

---

