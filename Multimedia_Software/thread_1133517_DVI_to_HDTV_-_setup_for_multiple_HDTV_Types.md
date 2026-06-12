---
title: "DVI to HDTV - setup for multiple HDTV Types"
date: 2009-04-23
forum: Multimedia Software
---

### Post by 4dplane on 2009-04-23
Hi,

I have a PC with Linux using a GeForce GT9400 graphics card. The card has DVI and HDMI output. What I want to be able to do is set up my Linux machine so the video works on any HDTV set that I connect it too. Right now when I connect to one HDTV it works just fine but when I connect it to another HDTV I have an overscanning issue where part of the screen is missing. So I assume if I connect it to a third HDTV I may or may not have a perfect looking screen.

Is there way to make my Linux machine more compatible with HDTV's? In Linux the video driver works with an xorg.conf file where a default file can be used or extra settings can be used like modeline settings. I have read this may fix my overscanning issue with one HDTV but could possible over heat a different HDTV with the incorrect modeline settings.

What if I used a DVI to Component adapter and then connected to the TV's.

How does Apple TV deal with this issue, there systems seem to work with HDMI DVI and Component. I do not have one so I do not know for sure, but I assume there system works with most TV's.

Thanks,
4dplane

---

### Post by tywashere on 2009-04-23
> **4dplane said:**
> Hi,

I have a PC with Linux using a GeForce GT9400 graphics card. The card has DVI and HDMI output. What I want to be able to do is set up my Linux machine so the video works on any HDTV set that I connect it too. Right now when I connect to one HDTV it works just fine but when I connect it to another HDTV I have an overscanning issue where part of the screen is missing. So I assume if I connect it to a third HDTV I may or may not have a perfect looking screen.

Is there way to make my Linux machine more compatible with HDTV's? In Linux the video driver works with an xorg.conf file where a default file can be used or extra settings can be used like modeline settings. I have read this may fix my overscanning issue with one HDTV but could possible over heat a different HDTV with the incorrect modeline settings.

What if I used a DVI to Component adapter and then connected to the TV's.

How does Apple TV deal with this issue, there systems seem to work with HDMI DVI and Component. I do not have one so I do not know for sure, but I assume there system works with most TV's.

Thanks,
4dplane

you made sure both tv's we're running correctly right? 
If so, the port on your card may be borked. to test this theory, try both TV's on both ports. if the one that works, had scanline problems on that port. then well. Problem solution found.

---

### Post by aeiah on 2009-04-23
xorg modelines can fix your overscanning issue but you'd need to configure each tv seperatley. basically the resolution is set correctly for HDTV but some HDTVs dont display all of the pixels; some are hidden behind the frame of the television.

im not sure if recent control panels by nvidia have a resize option but that's the path to go down. try launching 'nvidia-settings' and see if there's an option to adjust the image (but not the resolution).

if you want this because you're planning on taking your computer to your friend's houses etc then you may just want to find a simpler solution than messing with xorg you see. if the nvidia-settings program doesn't help then consider why you need to prevent overscanning. if its just because you dont want your movies cropped then you could consider just creating some mplayer settings or whatever that creates a black border in the part that the hdtv isnt displaying. if its for general desktop use you could consider sticking blank gnome panels around the edges so fullscreen apps dont go off the edges.

not very pretty i know, but if you're gonna be dealing with multiple HDTVs with multiple overscan sizes and nvidia-settings doesn't let you do anything then hacking xorg.conf will be a bitch.

---

### Post by 4dplane on 2009-04-23
> **tywashere said:**
> you made sure both tv's we're running correctly right? 
If so, the port on your card may be borked. to test this theory, try both TV's on both ports. if the one that works, had scanline problems on that port. then well. Problem solution found.

Are you saying I should try both TVs first with DVI and then HDMI connections to make sure they are consistent?


Thanks aeiah for the info, the blank gnome panel idea could do the trick. 

What about the DVI to Component idea? Would this change things in regards to being more compatible with HDTVs. I have two channel 12s in my area, one in analog and the other in digital. The analog displays perfectly on my screen but the one in digital has overscanning.

---

