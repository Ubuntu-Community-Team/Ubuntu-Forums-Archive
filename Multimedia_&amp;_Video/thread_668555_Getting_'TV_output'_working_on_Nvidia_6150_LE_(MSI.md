---
title: "Getting 'TV output' working on Nvidia 6150 LE (MSI Media Live)"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by djeddyg on 2008-01-15
Hi All,

I have recently built a combined MythTV back/frontend (specs below) based on an MSI Media Live basebones system. I'm really pleased with the system with a couple of exceptions, one of these being that no-matter what I do I simply cannot get any of the TV output connectors to provide a picture to my TV. This of course makes it a pretty crap PVR as I can't watch anything unless I bring a monitor in to the living room! :cry:

For a bit of background the case provides HDMI, Scart, s-video and composite outputs, from looking at the wiring I believe that these all come back to the same set of header pins on the motherboard, labelled 'TVJP1' if memory serves correctly. The MSI manual states that only one of these connectors can be used as the 'tv-output' at any given time, which seems reasonable, so that is what I am trying.

I am a newbie to linux and as such find manually modifying /etc/X11/xorg.conf somewhat daunting so I was pleased  to find out that xorg.conf can be configured through the 'nvidia-settings' gui, so far I have tried

1: Unplug all 'tv output' connectors from case.
2: Execute 'gksudo nvidia-settings'
3: In the resulting GUI select 'detect displays'. As expected the PC monitor is found but correctly identifies nothing else.
4: Connect my TV to the scart connector using a scart lead. TV is on and scart input is selected, nothing appears on the TV (as expected at this point).
5: Click 'detect displays' again, this time it correctly identifies that I have a TV plugged in to the scart socket (hoorah, now we're getting somewhere I think!).
6: I then configure the TV to clone my PC monitor, using twinview, at a resolution of 1024x768.
7: Select 'Save to X Configuration File' and overwrite my xorg.conf file.
8: Click 'apply', restart X etc - When I do this the TV momentarily flicks then it returns to a blank screen.

No errors are reported so I don't really know where to start looking, I have tried all manner of different ways of configuring the TV output such as selecting the separate X Server option in the GUI, using the s-video connector instead of scart etc but nothing works.

Could someone please point me in some useful beginning directions, or tell me what would be useful to provide (logs, xorg.conf etc)?

Look forward to hearing and trying out some suggestions from the Ubuntu/ Xorg Wizards out there!

Thanks,

Edd

Box specs:
CPU: AMD Athlon X2 64 BE-2350
MOBO: MSI
GFX: Onboard NVidia 6150 LE (using 128 MB of my main RAM)
RAM: 2GB Corsair
HDD: 750GB Samsung Spinpoint F1 SATA
Dist: Gutsy 7.10 AMD64
GFX Driver: I'm using the restricted nvidia driver identified as 'nvidia' in xorg.conf.

---

### Post by murchball on 2008-01-30
I'm not sure which output you're trying to use, but I got HDMI to work on mine. I don't remember exactly all of the steps that I took, but I know that I did everything through the GUI. I never got component to work properly; the color was way off and the resolution was way too low. 

HTH

---

### Post by Buster Charlie on 2008-04-18
> **murchball said:**
> I'm not sure which output you're trying to use, but I got HDMI to work on mine. I don't remember exactly all of the steps that I took, but I know that I did everything through the GUI. I never got component to work properly; the color was way off and the resolution was way too low. 

HTH



I ran into this problem with out component video out situations. The "Magenta screen of death"

Component video works FINE if you are using non Nvidia drivers (VESA?) but unfortunately a lot of programs seem to require some 3d acceleration. 

What I have discovered is that if you start unplugging component video cables, you do not get the standard component video degradation.
 For example, if you pull on cable it drops from magenta screen of death to a faded gray/tan  with faint color. If you pull another cable, you loose picture, but it's not the green sync cable.

So I have figured out what was happening (I've had this happen with windows also) 

The Nvidia drivers, break component video output, what in fact is happening is it is sending a S-VIDEO signal through the component cables.

So the ONLY solution when using nvidia drivers is to use S-video, not component video. 

This sucks.

I guess you might have some luck with a DVI to Component breakout adapter.

---

### Post by murchball on 2008-04-18
Recently, on another of my machines, I did get component out to work through the breakout cable of my GIGABYTE GV-NX73G256D-RH GeForce 7300GS. I did a fresh install of Mythbuntu and chose the proprietary driver and component out during the install. No fuss, no muss.

---

