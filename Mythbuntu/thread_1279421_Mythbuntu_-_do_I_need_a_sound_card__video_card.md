---
title: "Mythbuntu - do I need a sound card / video card"
date: 2009-09-30
forum: Mythbuntu
---

### Post by cat2005 on 2009-09-30
Hi,
 
I am very new to mythtv so forgive my ignorance.
 
Some research I have done mentioned (recommended) the following:
 
a)  Sound Card (is this the same as sound blaster ?)
b)  Video Card (is this the same as graphics card ?)
 
Why would I need these?  Doesn't the TV Tuner Card take care of audio and video (at least the digital TV Tuner Cards)?  
 
 *Could someone kindly explain why I need them, or why I do not need them (I already have "b" if "b" means "graphics card")?*
 
 _Here are my system specs_:
 
1 - Mythbuntu 9.04
2 - p4 cpu @ 2.4 ghz @ 300 - 400 bus
3 - 1 gb ram @ 300 - 400 bus
4 - Nvidia GeForce FX5200 @ 128 mb
5 - Asus mobo P4S800 (PCI support, no PCIe support)
6 - No Sound Card / Blaster
7 - Hauppauge PVR 150 (currently not setup with mythtv, but soon plan to replace this with something to capture both analog and digital)
8 - Want to display TV output on my computer monitor, currently using standard VGA cable to connect computer to monitor
9 - Speakers and sub-woof
10 - Digital cable via Time Warner
 
Thank you!

---

### Post by oldsoundguy on 2009-09-30
quick answer .. yes, you need a sound card .....
That is provided you can get it to work.  Haven't been able to get mine to talk and can find NO answer as to how to set it up and test it.  Doesn't seem to be a program in Mythbuntu to do so.  Maybe someone else can chime in with their experiences if they got a Blaster card to work (I have a 5.1 live).

---

### Post by movieman on 2009-10-01
Note that you don't specifically need a PCI sound card, on-board sound will do if your motherboard includes it and Linux supports it; I just use the on-board sound on my Atom motherboard and it works fine.

---

### Post by SiHa on 2009-10-01
The Tuner card will supply the Audio and Video **input** to the PC, in the form of (usually) an MPEG transport stream, which is then saved as an MPEG file. This is decoded by the PC when you want to watch it, and in order to output these to the TV, you need Video and Sound devices.

Your mobo has onboard sound, so as movieman states it should just be a case of configuring Myth to use it. The FX5200 will be fine for SD,  but not HD, unless you can get XvMC to work - I couldn't.

VDPAU is available currently as a backport for Mythtv 0.21which Mythbuntu 9.04 is), or it should be available in a few weeks with 0.22 (will be included in Mythbuntu 9.10).

If you want to use VDPAU for HD, you're limited. I've just been through this loop, and the only available card that will do VDPAU that is PCI, seems to be the 8400GS. I was trying to reuse an old shuttle pc, but I've ended up buying a new energy-efficient mobo and processor with built-in 8200 for VDPAU.

Probably more information than you need, but I thought the HD stuff may be relevant if you're considering any purchases. Hope this clears things up a bit.

---

### Post by cat2005 on 2009-10-01
movieman,
 
1) How can I determine if my motherboard's on-board sound will work with linux?  Is the only way to determine it to try it, or is there a listing somewhere that could tell me?
 
 
SiHa,
 
1) So, I assume I need VDPAU to make my graphics card function with mythtv, correct?  To get this, would I simply select the "backport" option in synaptic?
 
 
Thank you both.

---

### Post by SiHa on 2009-10-01
If you just want to watch Standard Def TV, then your graphics(the FX5200) will be fine - my frontend is exactly the same as this, except only a 2GHz P4. You don't need to do anything special to enable it, other than enabling the closed-source nVidia driver, which I think you can do during the Mythbuntu install.

If you want to watch High Def, then your processor alone does not have enough grunt, you would need hardware acceleration which would be provided by the graphics card. The current version of Mythtv that's in 9.04 (0.21) has the option to use XvMC (X-Video Motion Compensation), which will use your graphics hardware to accelerate the video decoding, and allow you to watch HD. There are a few issues with this, one being that you only get a B/W OSD, and you need a LOT of tweaks to get it working. I gave up.

The other option for HD is VDPAU, a new Linux API provided by nVidia to enable hardware video decoding of HD on it's later chipsets, mainly 8x00 and 9x00 series. So firstly you'd need a new graphics card that supports it. Then you would need to:
a) Use Jean-Yves Avenard's backport (don't ask me how, I haven't a clue, but there's plenty on this forum)
or
b) Wait a couple of weeks for Mythbuntu 9.10, which has Mythtv 0.22, and VDPAU or download the pre-release Alpha 6 from [here](http://www.mythbuntu.org/9.10/alpha6)

Also, I would say that, almost certainly, your integrated sound will work with Linux.

Go on - give it a go!

---

### Post by cat2005 on 2009-10-01
> **SiHa said:**
> If you just want to watch Standard Def TV, then your graphics(the FX5200) will be fine - my frontend is exactly the same as this, except only a 2GHz P4. You don't need to do anything special to enable it, other than enabling the closed-source nVidia driver, which I think you can do during the Mythbuntu install.
 
If you want to watch High Def, then your processor alone does not have enough grunt, you would need hardware acceleration which would be provided by the graphics card. The current version of Mythtv that's in 9.04 (0.21) has the option to use XvMC (X-Video Motion Compensation), which will use your graphics hardware to accelerate the video decoding, and allow you to watch HD. There are a few issues with this, one being that you only get a B/W OSD, and you need a LOT of tweaks to get it working. I gave up.
 
The other option for HD is VDPAU, a new Linux API provided by nVidia to enable hardware video decoding of HD on it's later chipsets, mainly 8x00 and 9x00 series. So firstly you'd need a new graphics card that supports it. Then you would need to:
a) Use Jean-Yves Avenard's backport (don't ask me how, I haven't a clue, but there's plenty on this forum)
or
b) Wait a couple of weeks for Mythbuntu 9.10, which has Mythtv 0.22, and VDPAU or download the pre-release Alpha 6 from [here]("http://www.mythbuntu.org/9.10/alpha6")
 
Also, I would say that, almost certainly, your integrated sound will work with Linux.
 
Go on - give it a go!
 
 
So, it seems I do not need to do anything to get my graphics and sound working.  
 
Correct?  
 
If so, then it appears the only task remaining is selecting an analog / digital tuner.

---

### Post by tonycollinet on 2009-10-02
Correct - but I wouldn't bother with an analogue tuner since analogue will be switched off in the near future.

(oops - UK centric post - analogue will be switched off in the UK - I have no idea where you are)

---

### Post by sabre2th on 2009-10-02
> **tonycollinet said:**
> Correct - but I wouldn't bother with an analogue tuner since analogue will be switched off in the near future.

(oops - UK centric post - analogue will be switched off in the UK - I have no idea where you are)
With Time Warner, the analog tuner will be fine unless you want to do HD.  You're limited to the 70-whatever channels that come with their standard cable package, but it works great.

Note: I have a Mythbuntu box with a PVR-500 (analog-only) running off Time Warner Digital Cable.  The box has an Athlon64 @ 2.2 GHz, 2 gigs of RAM, and a GeForce 6800GS.  It also uses onboard sound.  Granted, my specs are a bit higher, but I'm comfortable saying you shouldn't have any hardware problems.

---

