---
title: "Why is my HDMI output worse quality than my VGA output?"
date: 2008-11-21
forum: Mythbuntu
---

### Post by ElGeraldo on 2008-11-21
System setup:

Case : Antec Veris Fusion Black 430 (with the LCD, not VFD)
Mobo : ASUS M3A78-EM (ATI Radeon HD3200 / 780G chipset)
CPUs : AMD Athlon X2 4850e 2.5GHz
RAM  : GSKILL 2GB (2*1GB of DDR2 1066)
HDD  : WD6400AACS 640GB, SATA
DVD  : ASUS DRW-2014L1T, SATA
Tuner: HDHomerun ATSC, both inputs from a DB2 antenna
TV   : Samsung LN-S4095D 40" 1080p LCD HDTV
OS   : Mythbuntu 8.04.1, minimal changes to xorg.conf.

Has anyone noticed (i.e. not just people with the same motherboard as me) that the picture quality on the PC's HDMI video output is noticeably worse than what comes out of the VGA (D-Sub) connector?

If I watch live TV or recorded content, I notice that the picture quality from the HDMI output is nowhere near as good as that from the VGA output, which shouldn't be the case - the VGA connector is analog RGB+sync, whereas HDMI should be digital from hard disk to pixel on screen. I see a noisy, shadowy picture - much like watching a composite video signal through an audio cable rather than proper video coax. 

Also, the HDMI picture is about .25" smaller than the physical screen size all the way round. I haven't added any screen size tweaks to my xorg.conf nor manually changed any aticonfig command line settings. The only thing I've done is turn off the OpenGLOverlay to make it plays at the proper speed. Xfce control panel has the resolution set at 1920x1080, which was auto-detected when I set the the box up using the TV as a monitor, on the VGA interface. Mythfrontend setup shows the resolution as 1920x1080.

To get the system to output HDMI at all, I have to power off the PC and reboot with the HDMI connected. It then detects the TV on the HDMI port and I get video out of the HDMI.

I've also noticed that the VGA output is not as "nice" as watching the TV directly. It should be the same MPEG2 stream that's being used but the signal from the PC has pathetic black level (looks quite gray to me) and the colors are not at all saturated. Anyone else notice the same? Is this the norm for a Myth box?

---

### Post by jape42 on 2008-11-21
> 
Also, the HDMI picture is about .25" smaller than the physical screen size all the way round. 


yeah.  I've tried several versions of the ATI binary drivers and I can't get full screen 1:1 pixel mapping.  X thinks it is at 1920x1080 and the TV is receiving a 1080p60 signal, but there is a black border around the screen.

The radeonhd driver does not suffer from this (and hdmi audio worked better for me) but the radeonhd driver has no acceleration for my HD3200 graphics chipset.

I can't believe that after all this time, that ATI drivers are still in such a horrible state.


regards

jp

---

### Post by ElGeraldo on 2008-11-22
> **jape42 said:**
> The radeonhd driver does not suffer from this (and hdmi audio worked better for me) but the radeonhd driver has no acceleration for my HD3200 graphics chipset. Aha! Is the Radeon HD driver different from the fglrx driver? How do you install it? Can you watch videos at the proper frame rate?

I'm pretty much a newb to this Linux lark so just about any simple operation is difficult. If I get things too screwed up I just have to wipe the partition and reinstall because that takes less than an hour.

Some places I've read that people are using Xv and other places I've read that Xv isn't supported by ATI. What is Xv exactly? This is all so confusing.
> **jape42 said:**
> I can't believe that after all this time, that ATI drivers are still in such a horrible state.Me too. When I was looking for bits to build this HTPC, a friend told me to go with nVidia and I wish I'd listened. I only bought this motherboard because it had HDMI, DVI and VGA outputs, several PCI slots, etc.

---

### Post by jape42 on 2008-11-22
> **ElGeraldo said:**
> Aha! Is the Radeon HD driver different from the fglrx driver? 

Yes.  There are three different drivers for ATI chipsets.  One from ATI (has hardware acceleration) and two open source ones that only support acceleration on some ATI chipsets.  As far as I know only the fglrx has acceleration on the HD3200 because ATI has not yet released docs required to write a driver for it.

> 
How do you install it? 

You'd need to get their source and compile it.  If memory serves, HDMI audio was not included in their last release.
This is how I got started:
[http://www.mediaboxblog.co.uk/blog1.php/2008/10/03/howto-compiling-and-running-radeonhd](http://www.mediaboxblog.co.uk/blog1.php/2008/10/03/howto-compiling-and-running-radeonhd)

> 
Can you watch videos at the proper frame rate?

Not really.  I'm watching standard def so I've configured myth to change the resolution to 640x480 while playing back.  Since there is no hardware acceleration, the CPU must do all the scaling of the video.  My X2 5200 couldn't scale up to the resolution I wanted (1920x1080)


> 
I'm pretty much a newb to this Linux lark so just about any simple operation is difficult. If I get things too screwed up I just have to wipe the partition and reinstall because that takes less than an hour.

I'd say your best bet is to stick with something "standard" like the fglrx driver.  If VGA works for you, then I'd start with this, and revisit in a few monthes to see if anything has gotten better.


> 
Some places I've read that people are using Xv and other places I've read that Xv isn't supported by ATI. What is Xv exactly? This is all so confusing.

You can think of "Xv" support as "hardware video support".  Your HD3200 only has proper Xv support in the fglrx driver.

[http://en.wikipedia.org/wiki/X_video_extension](http://en.wikipedia.org/wiki/X_video_extension)

> 
Me too. When I was looking for bits to build this HTPC, a friend told me to go with nVidia and I wish I'd listened. I only bought this motherboard because it had HDMI, DVI and VGA outputs, several PCI slots, etc.


Don't feel too bad.  I did a lot of research before buying my MB, and still got burned by AMD/ATI. (and mplayer being limited to a single core...but that's another story).  I _knew_ nvidia was better supported, but there was so much going on at the time claiming nvidia had quality issues, I decided to go with ATI.

There is some hope though.  I sent an email to ATI asking about docs for the HD3200, and they claimed they were working on it.  Don't hold your breath though.

regards,

jp

---

### Post by groovietuner on 2008-11-22
> Has anyone noticed (i.e. not just people with the same motherboard as me) that the picture quality on the PC's HDMI video output is noticeably worse than what comes out of the VGA (D-Sub) connector?

Another thing to consider in regard to the image quality is the physical connection.  If it's possible, try using another source with the same cable to see if the cable is the issue (digital connections can be a pain).

> To get the system to output HDMI at all, I have to power off the PC and reboot with the HDMI connected. It then detects the TV on the HDMI port and I get video out of the HDMI.

Yep, this is pretty common (my nVidia mGPU is the same way (even on Vista)). I can't say for sure, but it seems to be an HDCP thing (only handshakes on initial boot).

Good luck.

---

### Post by Martje_001 on 2008-11-22
> **jape42 said:**
> There is some hope though.  I sent an email to ATI asking about docs for the HD3200, and they claimed they were working on it.  Don't hold your breath though.
That's actually true. Since AMD took over ATi, things got real better. See Phoronix for proof!

I believe them if the say so now.

---

### Post by ElGeraldo on 2008-11-24
Thanks to all for your input. After much forum reading, I have decided to stop wasting my time with this ATI joke of a graphics driver and buy an nVidia PCIe card with a DVI output. When I told my buddy that I was building an HTPC with Mythbuntu, he recommended getting an nVidia chipset but I ignored the advice. I wanted a motherboard with VGA, DVI and HDMI sockets built in. When I bought all my gear from NewEgg, the only mobo's that fit the bill had ATI graphics on them.

Come to think of it, my Windoze XP PC has an nVidia graphics card and it's rock solid. In contrast, my work XP laptop has built-in ATI graphics and it's only ever the ATI Catalyst software that causes BSODs.

Now I've just got to figure out which nVidia graphics card to get, buy it, install it and reinstall Mythbuntu for the 6th time :cool:

---

### Post by eightace on 2008-11-25
I have returned my prebuilt machine to the supplier and opted for Intel as opposed to ATI next time for the same reasons as you....[-(

---

