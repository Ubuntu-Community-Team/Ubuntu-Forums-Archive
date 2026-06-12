---
title: "Need a bit of help with NVIDIA TNT2 drivers"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by Disco Inferno on 2007-06-04
Hmm, I've been attacking this one for quite some time, and not Google nor any of the forums I've searched have been any help so far, so believe me I'm not posting without first searching.

Using Ubuntu 7.04, I can't get OpenGL acceleration(or any 2D accel for that matter) to appear to work. I've downloaded the legacy drivers and run the config to get 1024x768 resolution after enabling the driver in Restricted Drivers Manager, and yet... Screensavers don't show up at all, nothing but a black or white screen. Page scrolling is sluggish. Videos seem a tad too choppy. And I can't open any 3D-based games.

What I'm getting: appropriate resolution/refresh with good colour.

What I'm not getting: any sort of NVIDIA control panel(if there should be one, I don't know), any NVIDIA splash screen on startup, and as stated above, nothing appears to be accelerated.

I've tried running nvidia-settings in the Terminal, and all I get is a program called "nVidia Settings Configuration", which oddly seems to configure the nvidia-settings program, which I can't get to.

Err...

Bit of help anyone? I'm just a little out of my depth here. For what it's worth, everything else works as well as can be expected from Linux, no major issues elsewhere.

---

### Post by klabak on 2007-06-11
I'm getting the exact same problem. Tried using all other methods of installation, envy, manual, restricted drivers manager... etc. All I can get is a max resolution of 1024X768 using the restricted drivers mgr (the other methods do not work). I know this card can get higher res than that. No 3d acceleration, NVIDIA control panel or NVIDIA splash screen. Someone please help us!!!

---

### Post by SoloSalsa on 2007-06-12
And, a third person!  I seriously get no acceleration, and nothing above XGA (1024*768)8).

---

### Post by StitchJAcket on 2007-11-03
I guess this makes me number 4. I know this video card is capable of running some games that I am unable to get to run using the linux driver and using the legacy driver i get the worst resolution ever. I am currently running the gutsy dist. 7.10 and still nothing works. Please help someone or i am just going to give up and buy a new video card.

---

### Post by SoloSalsa on 2007-11-03
> **StitchJAcket said:**
> I guess this makes me number 4. I know this video card is capable of running some games that I am unable to get to run using the linux driver and using the legacy driver i get the worst resolution ever.
I hear ya.  It still sucks for me, too.  Actually, I'm only getting SVGA (800x600) with the proprietary legacy driver.  I heard that I need to enter proper refresh rates, so I've tried, but then X says the config is corrupt or something, and I can't get anything graphical unless I restore backed-up settings.  So, I'm just using no driver (is that called VESA or something?), and rates are real bad.
I really hate this.  The TNT, TNT2 are so old, that it should not harm the company at all if they just opened them completely.  Also, these old chipsets (also the RAGE series from ATI, which has even worse compatibility) were often integrated in to motherboards and laptops, or came with low end retail computers.  I have five of these (an auction lot; I'm using two, and three gathering dust), and they are worthless to sell back.  I had no idea how bad they would be when I was buying...

---

### Post by Mountlake_Cut on 2007-11-17
I was having the same problem with my Diamond Viper (Nvidia TNT/TNT2) card and Ubuntu 7.10 Gutsy.
I finally found a link to Shevin's blog site in the Launchpad? Tech area. I followed
his instructions listed on the page and everything works great now. Here's the address
to the page :

[http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html](http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html)

It was pretty easy to follow, just remember to find the correct refresh rates for
your monitor.

---

