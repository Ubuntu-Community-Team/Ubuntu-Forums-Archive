---
title: "HDTV as monitor 720P resolution??"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by Aquaman420 on 2008-02-03
What would I set the resolution for a 32" 720P HDTV.  Any thoughts advice opinions on the resolutuion or what TV to get is always appreciated.  Thanks

---

### Post by rsidle on 2008-02-03
Need a little more info: What is your video card, how are you connecting (VGA cable or DVI to HDMI)? I've had pretty good luck with Nvidia cards and a VGA connection, slightly worse luck with nvidia card and DVI/HDMI connection.

---

### Post by Aquaman420 on 2008-02-03
Thank you for the reply.  I have an ATI 1650xt.  I was going to connect it with the DVI to HDMI converter.  I have one left from my HD cable box.  I am not to new to all this but I got confused because the res. of my 22" widescreen monitor is 1680x1050 but yet the res of a 32" hdtv says it is 1366x768.  It doesn't make much sense to me unless the TV is going by a different standard or something.

---

### Post by rsidle on 2008-02-03
Ok... yes the tv has lower resolution than your monitor. Seems kinda counter-intuitive I know. With my nvidia card going via vga cable to a 32" 720p lcd tv it sucessfully auto detects a resolution of 1366x768. With another system using nvidia card via DVI/HDMI cable to 720p plasma it overscans to 1280x800. I'd advise you to set the resolution on the computer to something low like 1024x768 *before* you connect it to the TV, and then set it to 1366x768. That way, you won't get left with your tv saying "cannot display this resolution." I've only had experience with nvidia cards, so I'm afraid this is about all the info I can give you. :)

---

### Post by Aquaman420 on 2008-02-03
No thank you very much.  I still got some time to wait until BestBuy runs a 3 year no interest promo again.  So I will be doing more research.  What kind of TV do you have by chance? Also thank you for the tip about the lower res.  I have defintely seen the "out of range" before not to fun.

---

### Post by izak on 2008-02-04
Hi

I'm also trying to get my Ubuntu, geforce 2 equipped PC to display on my 1366x768 LCD via VGA cabel. 

It works great at 1024x768 with borders on the sides, but how do I change the resolution to 1366 to get widescreen? On the standard screen-resolution menu none of the available resolutions are widescreen (1024x768, 800x600, 640x480). Is there some non-GUI way to force widescreen output? Or am I strictly limited to the options in the menu?

Thanks!

[EDIT]
OK, I've found [this]("http://ubuntuforums.org/showthread.php?t=686686&highlight=widescreen+resolution") thread where they claim nvidia-settings (with gksudo from the command line I suppose) can sort this out. Will try tonight...

---

### Post by rsidle on 2008-02-04
> **izak said:**
> Hi

I'm also trying to get my Ubuntu, geforce 2 equipped PC to display on my 1366x768 LCD via VGA cabel. 

It works great at 1024x768 with borders on the sides, but how do I change the resolution to 1366 to get widescreen? On the standard screen-resolution menu none of the available resolutions are widescreen (1024x768, 800x600, 640x480). Is there some non-GUI way to force widescreen output? Or am I strictly limited to the options in the menu?

Thanks!

[EDIT]
OK, I've found [this]("httphttp://ubuntuforums.org/showthread.php?t=686686&highlight=widescreen+resolution") thread where they claim nvidia-settings (with gksudo from the command line I suppose) can sort this out. Will try tonight...

Yep, the nvidia gui is pretty good. It usually has the correct resolutions available. You should be golden.

---

### Post by izak on 2008-02-05
Unfortunately it didn't work, in fact I am now a step back from where I was. Previously I used a borrowed cable to test it and got up to 1024x768, but yesterday I bought a 5m VGA cable and now the screen is autodetected as a 640x480 CRT! 

Even in the nvidia-settings gui the only resolution options are 640x480 and 320x240. So the problem is with X incorrectly recognising the screen. Any ideas on how I can force the screen to be identified as the correct resolotion?

---

### Post by izak on 2008-02-05
OK, I did a bit of digging. Tonight I'm going to try the tips in the [FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto"). [This]("http://ubuntuforums.org/showthread.php?t=687438") thread also seems useful.

---

### Post by izak on 2008-02-06
The very first point (Undetected Monitor Specs)  from the [FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto") was what was required to force correct identification of the monitor. Basically I had to manually specify the HorizSync  and  VertRefresh rates.  

Unfortunately I didn't have the correct HorizSync and  VertRefresh values so it took 3 hours of trying all the other solutions before guessing the ranges resulted in getting 1027x768 resolution back (as oppoised to 640x480).

Attempting a the newly available widescreen resolution from nvidia-settings resulted in a black screen. However I think this is because the guessed HorizSync and  VertRefresh ranges are incorrect, so after downloading the Bravia's manual I'll try again with the correct values tonight. 

*fingers crossed* :)

---

### Post by izak on 2008-02-12
After specifying the exact refresh rates in the TV's monitor (not ranges, just single numbers: HorisonSync 47.8, VertSync 60) the display is in beautiful widescreen, but at low resolution. nvidia-settings allows one to then adjust the resolution.

The weird thing is, the maximum resolution available from nvidia settings is 1280x768, while my screen resolution is 1380x768. I dont know how to change this. I tried looking at the xorg.conf nvidia-settings generates, which basically includes a line called something like "meta 1280x768" in the screen options. However pasting this into my own xorg.conf just results in a black screen. As previously mentioned, substituting my xorg.conf with the one nvidia-settings generates also breaks the windowing system. 

Any ideas on how to get 1380x768 resolution? 1280x768 looks fine, but the correct resolution would be better...

---

