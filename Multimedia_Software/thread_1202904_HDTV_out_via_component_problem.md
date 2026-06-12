---
title: "HDTV out via component problem"
date: 2009-07-02
forum: Multimedia Software
---

### Post by tidan on 2009-07-02
Hi,
I'm not getting the correct picture via my TV out(component) connected to my HDTV (1080i). In XBMC Its only a blank screen.
In Ubuntu its just a greenish still shot of the desktop in very poor resolution/color.  
The bios shows up as does the initial splash screen, then it goes bad.
Is is possible my video card is not supported?

I'm using the following hardware:
- P4 2.5Ghz (MB supports AGP4x only)
- 5GB RAM
- 80GB IDE HDD
- BFG Nvidia Geforce 7300GT 512MB AGP 8x (connected via Component Dongle out)
- Turtle Beach Riviera - (connected via optical out)
- 350 watt powersupply

I'm also having some audio issues that I'll post in a new thread titled as such.

Thanks for any help you can offer!

---

### Post by armitage374 on 2009-07-03
I'm not completely sure what you are trying to do here, but I think you may be using the wrong resolution. Here's why:
 
Component is not digital and thus is not the same quality.
 
If your component is standard tv out, then the resolution you are spitting out is a maximum of 720x576 pixels (I'm basing of from pal signals here as I am in Europe, you can find the right resolution for other regions on wiki). 
 
In comparison a Digital signal as HDMI is 1920x1080 pixels.
 
If you want a 1920x1080 resolution without using a HDMI or DVI connector, you'll need two things:
1: A graphics card that supports said resolution and 
2: A television with a pc in port (you know, a VGA port).
 
After connecting the television and the computer, set the resolution to what you want.
 
If you are still not getting a signal, you'll need to check the resolution specs for your television. 
 
It may be that your television is not a "Full HD1080" television but only "HD Ready"
 
If your television is only "HD Ready", then it can only run a max resolution of 720x12?? pixels, the socalled 720p format. It's a transition format.
 
NB: If you use the PC port for connection, be advised that you'll need to run extra cables for sound.

---

### Post by tidan on 2009-07-03
Thanks for the reply!
What I'm attempting to do is create a HTPC using linux.  I would like to invest the money on this idea for a PC instead of a new blueray player ;-)

My goals are to have a system that will send out 1080i video to my 1080i capable TV;  send out bitstream audio via optic(toslink) to my DTS/AC3 reciever in both 48khz and 44khz - I have many DTS conversions I've done of stereo material that are all in 44khz DTS now.  

In answer to your questions,  my TV is 100% true 1080i HD LCD.   I currently use component in for everything and recieve true HD signal from my other pieces of hardware.

Interestingly,  I've spent 4 days straight working on getting Ubuntu to output HD to my TV and digital audio out via SPDIF(toslink) to my reciever with no luck.   
Last night I tossed in a Winblows install and it took about 15 minutes and everything worked (except for the 44khz DTS streaming).  

I really wanted to get away from Bimbows but I'm losing patience and money on this pursuit of a Linux based HTPC.

---

