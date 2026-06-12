---
title: "Preferred solution: DVI-HDMI or VGA to 42&quot; Plasma TV ?"
date: 2007-12-20
forum: Mythbuntu
---

### Post by rune.evjen on 2007-12-20
I have a Mythbuntu setup on an ACER L250 Media Center PC with a PVR-500 card and an integrated ATI card.

This card supports both VGA and DVI output.

I want to connect this to a Panasonic Plasma TV (TH42-PV70) which has a native resolution of 1024x768.

When connecting the Plasma Screen with a VGA cable, it reports the standard PC resolutions, up to 1024x768

When connecting it through a DVI to HDMI cable, it report the standard TV resolutions (ex 720x576 50 and 60Hz) as well as the native resolution of 1024x768.

I have been experiecting a bit to see what gives the best display of Standard definition PAL.

Using VGA my resolution was set to 1024x768.
Using DVI-HDMI, I tested using 1024x768 for menus and video, as well as making MythTV switch to 720x576 for TV playback.

It seems like the VGA setup gives a clearer picture, but with interlacing effect. Adding a deinterlacing filter under MythTV Setting - TV Playback helps somewhat but the effect is not completely gone. It seems like my TV deinterlaces the PAL signal from my cable provider better.

Using DVI-HDMI I get no interlacing effect, it seems like the TV is deinterlacing the input on the HDMI port, but the picture gets more "blurry".

Can anybody help with user experiences on VGA vs DVI-HDMI ?

Is the interlacing assumption correct ?

Many thanks, 

Rune

---

### Post by tgalati4 on 2007-12-20
Probably.  Look in the advanced video settings of the TV.  Many have noise and scaling filters as well.  See if you can turn them off and see if there is a difference.

The VGA port is normally used for showing static content--slide shows, pictures of your kids, etc.  Therefore its scaling and filtering options may be limited.  One other test to run is to get a DVI-to-VGA connector (usually the graphics card comes with them) and run from the DVI of the graphics card to the VGA input of the TV.  That may give you the a clearer picture.

Thanks for sharing your experiences.

---

### Post by afljafa on 2007-12-20
If your card can do component (usually via SVideo breakout) i`d give that ago. I get 1080 and trust me - the video playback is much much better than both VGA and HDMI.

---

### Post by rsambuca on 2007-12-20
A few things here...

Both the VGA and HDMI/DVI will be sending non-interlaced signals to the tv.  In order to get rid of interlacing artifacts from interlaced video recorded to your PC, you will need to do the de-interlacing on your PC, as the TV should be just passing the signal through.  If the DVI input doesn't show it and looks fuzzy, that is just due to settings on your TV, ie sharpness.

VGA signal is analog, whereas the DVI signal is digital.  If the VGA cable is quality and shielded adequately, then the pictures should be similar, although the general concensus is that digital signals are better.

---

### Post by nelsonmuntz on 2008-06-15
I'm certainly an advocate of digital signals over analog in theory, but my experience to date has been much better using a VGA connection than DVI/HDMI, based on the devices I have at hand.

With VGA output, I was able to achieve my TV's native resolution of 1360x768 after messing with some utilities. However, on introducing an A/V amp (Onkyo TX-SR605) into the mix and connecting the PC to the AMP via DVI/HDMI and amp to TV via HDMI, I've had no end of trouble.

* I can't achieve 1360x768 resolution (don't know for certain, but I think this may be a shortcoming of the amp). 
* The shadows are much too dark using HDMI - adjusting the brightness doesn't fix this - it just washes out the highlights. I was able to improve this somewhat with the ATI drivers in Windows, but not so under Linux to date. Oddly enough, when switching the colour temperature setting on my TV (ViewSonic) from Cold to Standard, the picture momentarily comes good, then goes dark again! Grrrr
* When setting up Mythbuntu, I had the PC connected to a 20" LCD display running at 1600x1200. Now it is connected to my amp instead and I try to keep the resolution set to 1280x768. However, when switching the amp source away from the PC to something else, the PC somehow registers this and jumps back to 1600x1200. God knows why! This in turn causes all sorts of other issues I won't go into.
* Picture quality is poorer on HDMI than VGA due to the extra scaling steps taking place. I have no control over this within any of my devices it seems. :(

Sadly, my amp has no VGA input/output, so unless I opt for needing to use two different source selectors (amp and TV - the latter of which requires multiple menu navigation, for Pete's sake!!!!!), I'm stuck with HDMI and the problems above.

Such is life.

---

### Post by Trollslayer on 2008-06-15
DVI->HDMI, definitely.
I do that and set the colour mode to automatic.
HDMI is DVI plus digital audio - HDCP which is the encryption can be present on either.

---

### Post by peterbrewer on 2008-06-15
> **rsambuca said:**
> A few things here...

Both the VGA and HDMI/DVI will be sending non-interlaced signals to the tv.  In order to get rid of interlacing artifacts from interlaced video recorded to your PC, you will need to do the de-interlacing on your PC, as the TV should be just passing the signal through.  If the DVI input doesn't show it and looks fuzzy, that is just due to settings on your TV, ie sharpness.

VGA signal is analog, whereas the DVI signal is digital.  If the VGA cable is quality and shielded adequately, then the pictures should be similar, although the general concensus is that digital signals are better.

There is no benefit for digital unless it is over a larger distance.  The location of the PC will influence the choice of cable.

---

### Post by Trollslayer on 2008-06-15
> **peterbrewer said:**
> There is no benefit for digital unless it is over a larger distance.  The location of the PC will influence the choice of cable.

On the contrary, digital means that timing is pixel perfect and this does help.
For what it's worth, I use a lot of HDMI cables at work and until you get up to 1080p at 10-15 metres the cheap cables work perfectly well.

---

