---
title: "Problem starting X with nvidia"
date: 2009-06-28
forum: Mythbuntu
---

### Post by thegooch49 on 2009-06-28
Hi! I'm having some X issues with various Nvidia cards with mythbuntu 9.04. I have tried 3 different cards. A GeForce 6 series, a QuadroFX 1450, and a GeForce 8800GT. Using the live CD, the only card that will successfully start X on the live CD is the GeForce 6. The others just spit me out to text mode. 

Any ideas why the other cards won't work? I would just stick with the 6, but it's the oldest of all the cards I have. I couldn't get the 6 to work with the proprietary nvidia drivers either. When I load them, I get no output to my monitor. Just 'DVI cannot display this mode'. 

Any suggestions on getting the other cards to work? Or any suggestions on how to get the 6 to work with the proprietary drivers (so I can use Xv)? 

Many thanks for any help.

---

### Post by jaakan on 2009-06-28
Have you tried installing with the NV GF6XX, install the NV drivers, and swaping the card for the GeForce 8800GT?

---

### Post by thegooch49 on 2009-06-28
Hi, thanks for the reply. So with the 6800 installed, I installed the proprietary drivers. I left the 6800 card installed to see what it looked like. It looked pretty good. So I shutdown and installed the 8800GT card. When X tries to start, I get an error that says:

EE NV: Failed to determine the amount of available video memory
EE Screens found, but none have a usable configuration

So I'm still at no-go with the 8800. I can keep with the 6800GTO, but I am thinking that the 8800 might be a bit better at playback. The 6800 taxes the CPU pretty hard watching HD. I'm wondering if a more able card like the 8800 will help a bit. 

Any more suggestions? Thanks again for the help.

---

### Post by ian dobson on 2009-06-29
Hi,

If the 8800 supports VDPAU (I think it does) then maybe have a look at using the VDPAU backports.

I'm running my frontend on an underclocked C2D (1.2GHz) and a 9300GT graphic card and the CPU load is only 10% or so watching HD programs.

Regards
Ian Dobson

---

