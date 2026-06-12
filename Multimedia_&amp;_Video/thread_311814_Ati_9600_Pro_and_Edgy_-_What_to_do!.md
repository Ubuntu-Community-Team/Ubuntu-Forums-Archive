---
title: "Ati 9600 Pro and Edgy - What to do!"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by RudolfMDLT on 2006-12-03
Hi,

If you can help me setup my card I will be grateful but I have written my own how to(see my sig) so i think I am competent enough with that.

The thing is that some Ati cards, mine included can't render in Edgy - you have to disable Composite rendering and thus no transparency in KDE and no Compiz/Beryl. Where's the fun in that?

What I would like to know is what to do now:

1) Buy a new Nvidia card and flog the Ati one because the 9600 will never be supported

2) Chill out, there is a driver on it's way within the next 3 months that will make this nasty problem go away.

3) Neither Ati nor the Nvidia cards(Geforce 6600LE or Geforce 4 Fx 6200) are supported in Edgy so you have to upgrade your system to an PCI-X system.

4)?

Option 4 is open for anybody who can see an option 4.

I shall greatly appreciate any comments or advice.

Thanks,

Rudolf

---

### Post by Forceflow on 2006-12-03
I got my Radeon 9600 pro to work in Edgy, though. Read the BinaryDriverHowTo on the wiki. The Binary Driver readmy explicitly states that the card is supported, right ?

I might be totally wrong though. I didn't check whether or not the 3D accell worked.

---

### Post by RudolfMDLT on 2006-12-03
Thanks! My card does work... but not very well.

in the terminal do: glxgears -printfps

it should be around 2000 not 250!
 
1228 frames in 5.0 seconds = 245.424 FPS

I would appreciate it if you could try yours?


Any other comments welcomed!
(This is polite English for PLEASE HELP ME NOW! :) )

Cheers,

Rudolf

---

### Post by Shatrat on 2006-12-03
Well, I just recently upgraded my old 9600 pro for a used 6800 on ebay for 69 bucks and I'm pretty glad I did.

If youre getting so few fps in glxgears its pretty sure that you dont have direct 3d rendering.  
If you type glxinfo | grep rendering it should say Direct Rendering: No or something like that?

There are plenty of how-to threads on these forums and others about getting ATI drivers to work.  Personally, I'll never use ATi again.  Nvidia drivers are so much better, the beta ones support the composite stuff for Beryl natively without having to mess with XGL, performance and IQ in games is better....et cetera.  Also, it doesnt cost much to get a card that will blow the doors off a 9600 pro.

Good luck whatever direction you go.

---

